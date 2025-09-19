# 📦 插件依赖管理系统

现在的Python依赖包管理依然存在问题，请保留你的`python_dependencies`属性，等待后续重构。

## 📚 详细教程

### PythonDependency 类详解

`PythonDependency`是依赖声明的核心类：

```python
PythonDependency(
    package_name="PIL",          # 导入时的包名
    version=">=11.2.0",          # 版本要求
    optional=False,              # 是否为可选依赖
    description="图像处理库",     # 依赖描述
    install_name="pillow"        # pip安装时的包名（可选）
)
```

#### 参数说明

| 参数 | 类型 | 必需 | 说明 |
|------|------|------|------|
| `package_name` | str | ✅ | Python导入时使用的包名（如`requests`） |
| `version` | str | ❌ | 版本要求，使用pip格式（如`>=1.0.0`, `==2.1.3`） |
| `optional` | bool | ❌ | 是否为可选依赖，默认`False` |
| `description` | str | ❌ | 依赖的用途描述 |
| `install_name` | str | ❌ | pip安装时的包名，默认与`package_name`相同，用于处理安装名称和导入名称不一致的情况 |

#### 版本格式示例

```python
# 常用版本格式
PythonDependency("requests", ">=2.25.0")           # 最小版本
PythonDependency("numpy", ">=1.20.0,<2.0.0")       # 版本范围
PythonDependency("pillow", "==8.3.2")              # 精确版本
PythonDependency("scipy", ">=1.7.0,!=1.8.0")       # 排除特定版本
```

