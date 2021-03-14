# g-cz-emoji

> 中文版本符合 Angular commit 规范的 git-cz emoji 提示

**g-cz-emoji** allows you to easily use emojis in your commits using [commitizen].

```sh
? 选择提交的更改类型：
❯ feat      🌟  引入新特性
  fix       🐞  修复 Bug
  docs      📚  写文档
  refactor  🎨  重构代码
  chore     🔩  杂事修改
```

## 安装

**全局**

```bash
npm install --global g-cz-emoji

# 设置为项目的默认适配器
echo '{ "path": "g-cz-emoji" }' > ~/.czrc
```

**本地**

```bash
npm install --save-dev g-cz-emoji
```

添加到本地项目的 `package.json`:

```json
"config": {
  "commitizen": {
    "path": "g-cz-emoji"
  }
}
```

## 使用

```sh
$ git cz
```

## Customization

默认情况下，`g-cz-emoji` 已经可用。对于不同用户使用方法可能有所不同，因此有一些配置选项可以根据项目需要进行微调。
作者在项目中的配置如下：
` { "g-cz-emoji": { "skipQuestions": [ "issues", "body" ] }`

### 如何使用

配置 `g-cz-emoji` 可以在用户主目录 (`~/.czrc`) 中处理，影响所有项目的变更。或者对于每个项目的单独配置可以在(`package.json`)处理。只需将如下所示的配置属性添加到具有重写设置的任意位置的现有对象中。
```json
{
  "config": {
    "g-cz-emoji": {}
  }
}
```

### 配置选项

#### Types

默认情况下 `g-cz-emoji` 配置了符合 Angular 规范的并且在
[Gitmoji](https://gitmoji.carloscuesta.me/) 中的 commit 类型。

An [Inquirer.js] 你可以自定义类型数组:

```json
{
  "config": {
    "g-cz-emoji": {
      "types": [
        {
          "emoji": "🌟",
          "code": ":star2:",
          "description": "A new feature",
          "name": "feat"
        }
      ]
    }
  }
}
```

#### Scopes

An [Inquirer.js] choices array:

```json
{
  "config": {
    "g-cz-emoji": {
      "scopes": ["home", "accounts", "ci"]
    }
  }
}
```

#### Symbol

一个布尔值，允许在提交消息中使用 unicode 值而不是默认的 [Gitmoji](https://gitmoji.carloscuesta.me/)标记。Symbol 的默认值为 true。

```json
{
  "config": {
    "g-cz-emoji": {
      "symbol": false
    }
  }
}
```
#### conventional

一个布尔值，是否保持传统提交类型，允许在提交消息中保持 type 的同时直接将 [Gitmoji](https://gitmoji.carloscuesta.me/) 中的 emoji 内容到 message 中。 conventional 的默认值为 true。

```json
{
  "config": {
    "g-cz-emoji": {
      "conventional": true
    }
  }
}
```

例子：

```bash
# true
fix: 🐛  fix a bug
# false
🐛   fix a bug
```
#### Skip Questions

你想要跳过的一系列问题:

```json
{
  "config": {
    "g-cz-emoji": {
      "skipQuestions": ["scope", "issues"]
    }
  }
}
```

你可以跳过以下问题: `scope`, `body`, `issues`, 和 `breaking`。`type` 和 `subject` 是必填项。



#### Customize Questions

包含原始问题覆盖的对象:

```json
{
  "config": {
    "g-cz-emoji": {
      "questions": {
        "body": "This will be displayed instead of original text"
      }
    }
  }
}
```

#### Customize the subject max/min length

你想要的主题的最大长度/最小长度：

```json
{
  "config": {
    "g-cz-emoji": {
      "subjectMaxLength": 200,
      "subjectMinLength": 5,
    }
  }
}
```

## Examples

- https://github.com/Falieson/TRAM

## Commitlint

Commitlint can be set to work with this package by leveraging the package https://github.com/arvinxx/commitlint-config-gitmoji.

```bash
npm install --save-dev commitlint-config-gitmoji
```

_commitlint.config.js_

```js
module.exports = {
  extends: ['gitmoji'],
  parserPreset: {
    parserOpts: {
      headerPattern: /^(:\w*:)(?:\s)(?:\((.*?)\))?\s((?:.*(?=\())|.*)(?:\(#(\d*)\))?/,
      headerCorrespondence: ['type', 'scope', 'subject', 'ticket']
    }
  }
}
```

## License

MIT © guowenfh

[commitizen]: https://github.com/commitizen/cz-cli
[inquirer.js]: https://github.com/SBoudrias/Inquirer.js/
