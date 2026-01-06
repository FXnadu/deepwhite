# Mermaid 图表全宽展示测试

这个文档用于测试 DeepWhite 主题中 mermaid 图表的全宽展示功能。

## 1. 普通代码块测试

下面是一个普通的 JavaScript 代码块，应该保持在写作区域的宽度限制内：

```javascript
// 这是一个普通的代码块
function calculateSum(a, b) {
    return a + b;
}

const result = calculateSum(10, 20);
console.log(`计算结果: ${result}`);

// 这个代码块应该保持在 80ch 的宽度限制内
const longVariableName = "这是一个很长的字符串，用来测试代码块的宽度限制是否正常工作";
```

## 2. Mermaid 流程图测试

下面是一个 mermaid 流程图，应该突破宽度限制，全宽展示：

```mermaid
graph TD
    A[开始] --> B{是否登录?}
    B -->|是| C[显示主页]
    B -->|否| D[跳转登录页]
    D --> E[输入用户名密码]
    E --> F{验证成功?}
    F -->|是| G[设置登录状态]
    F -->|否| H[显示错误信息]
    H --> E
    G --> C
    C --> I[用户操作]
    I --> J{需要权限?}
    J -->|是| K[检查权限]
    J -->|否| L[执行操作]
    K -->|有权限| L
    K -->|无权限| M[显示权限不足]
    L --> N[操作完成]
    M --> I
    N --> O[结束]
```

## 3. Mermaid 时序图测试

```mermaid
sequenceDiagram
    participant 用户
    participant 前端
    participant 后端
    participant 数据库
    
    用户->>前端: 点击登录按钮
    前端->>前端: 验证表单数据
    前端->>后端: 发送登录请求
    后端->>后端: 验证用户凭据
    后端->>数据库: 查询用户信息
    数据库-->>后端: 返回用户数据
    后端->>后端: 生成JWT令牌
    后端-->>前端: 返回登录结果
    前端->>前端: 保存令牌到本地存储
    前端-->>用户: 显示登录成功消息
    前端->>前端: 跳转到主页
```

## 4. 普通 Python 代码块

这是另一个普通代码块，用于对比：

```python
# Python 代码示例
class UserManager:
    def __init__(self):
        self.users = {}
    
    def add_user(self, username, email):
        """添加新用户"""
        if username not in self.users:
            self.users[username] = {
                'email': email,
                'created_at': datetime.now(),
                'active': True
            }
            return True
        return False
    
    def get_user(self, username):
        """获取用户信息"""
        return self.users.get(username, None)

# 使用示例
manager = UserManager()
manager.add_user("张三", "zhangsan@example.com")
user_info = manager.get_user("张三")
print(f"用户信息: {user_info}")
```

## 5. Mermaid 甘特图测试

```mermaid
gantt
    title 项目开发时间线
    dateFormat  YYYY-MM-DD
    section 需求分析
    需求收集           :done,    des1, 2024-01-01,2024-01-05
    需求分析           :done,    des2, 2024-01-06, 2024-01-10
    需求评审           :done,    des3, 2024-01-11, 2024-01-12
    section 设计阶段
    系统设计           :active,  des4, 2024-01-13, 2024-01-20
    UI设计            :         des5, 2024-01-15, 2024-01-25
    数据库设计         :         des6, 2024-01-18, 2024-01-22
    section 开发阶段
    前端开发           :         dev1, 2024-01-23, 2024-02-15
    后端开发           :         dev2, 2024-01-26, 2024-02-20
    接口联调           :         dev3, 2024-02-16, 2024-02-25
    section 测试阶段
    单元测试           :         test1, 2024-02-21, 2024-02-28
    集成测试           :         test2, 2024-02-26, 2024-03-05
    用户验收测试        :         test3, 2024-03-06, 2024-03-10
```

## 6. 对比总结

通过上面的测试，你应该能看到：

- **普通代码块**：保持在写作区域的宽度限制内（约80个字符宽度）
- **Mermaid图表**：突破宽度限制，占据全屏宽度，更好地展示复杂图表

这样的设计既保持了文本内容的可读性，又让图表有足够的空间展示详细信息。