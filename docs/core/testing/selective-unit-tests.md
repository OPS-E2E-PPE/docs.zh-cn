---
title: 运行选择性单元测试
description: 如何使用筛选表达式通过 .NET Core 中的 dotnet 测试命令运行选择性单元测试。
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728184"
---
# <a name="run-selective-unit-tests"></a>运行选择性单元测试

借助 .NET Core 中的 `dotnet test` 命令，可以使用筛选表达式来运行选择性测试。 本文演示如何筛选运行哪些测试。 下面的示例使用 `dotnet test`。 如果使用的是 `vstest.console.exe`，请将 `--filter` 替换成 `--testcasefilter:`。

## <a name="character-escaping"></a>字符转义

在 `*nix` 上使用包含感叹号 (!)的筛选器需要转义，因为保留了 `!`。 例如，如果命名空间包含 IntegrationTests `dotnet test --filter FullyQualifiedName\!~IntegrationTests`，则此筛选器将跳过所有测试。
请注意感叹号前面的反斜杠。

对于包含泛型类型参数的逗号的 `FullyQualifiedName` 值，请使用 `%2C` 来转义逗号。 例如：

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a>MSTest

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| 表达式 | 结果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 运行 `FullyQualifiedName` 包含 `Method` 的测试。 在 `vstest 15.1+` 中可用。 |
| `dotnet test --filter Name~TestMethod1` | 运行名称包含 `TestMethod1` 的测试。 |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | 运行属于类 `MSTestNamespace.UnitTest1` 的测试。<br>**注意：** 由于 `ClassName` 值应有命名空间，因此 `ClassName=UnitTest1` 无效。 |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | 运行除 `MSTestNamespace.UnitTest1.TestMethod1` 之外的其他所有测试。 |
| `dotnet test --filter TestCategory=CategoryA` | 运行含 `[TestCategory("CategoryA")]` 批注的测试。 |
| `dotnet test --filter Priority=2` | 运行含 `[Priority(2)]` 批注的测试。<br>

**使用条件运算符 | 和 &amp;**

| 表达式 | 结果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | 运行 `FullyQualifiedName` 包含 `UnitTest1` 或 `TestCategory` 是 `CategoryA` 的测试  。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | 运行 `FullyQualifiedName` 包含 `UnitTest1` 且 `TestCategory` 是 `CategoryA` 的测试  。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 运行 `FullyQualifiedName` 包含 `UnitTest1` 且 `TestCategory` 是 `CategoryA` 或 `Priority` 是 1 的测试   。 |

## <a name="xunit"></a>xUnit

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| 表达式 | 结果 |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | 仅运行一个测试，即 `XUnitNamespace.TestClass1.Test1`。 |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | 运行除 `XUnitNamespace.TestClass1.Test1` 之外的其他所有测试。 |
| `dotnet test --filter DisplayName~TestClass1` | 运行显示名称包含 `TestClass1` 的测试。 |

在代码示例中，包含键 `Category` 和 `Priority` 的已定义特征可用于筛选。

| 表达式 | 结果 |
| ---------- | ------ |
| `dotnet test --filter XUnit` | 运行 `FullyQualifiedName` 包含 `XUnit` 的测试。  在 `vstest 15.1+` 中可用。 |
| `dotnet test --filter Category=CategoryA` | 运行包含 `[Trait("Category", "CategoryA")]` 的测试。 |

**使用条件运算符 | 和 &amp;**

| 表达式 | 结果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | 运行 `FullyQualifiedName` 包含 `TestClass1` 或 `Category` 是 `CategoryA` 的测试  。 |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | 运行 `FullyQualifiedName` 包含 `TestClass1` 且 `Category` 是 `CategoryA` 的测试  。 |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | 运行 `FullyQualifiedName` 包含 `TestClass1` 且 `Category` 是 `CategoryA` 或 `Priority` 是 1 的测试   。 |

## <a name="nunit"></a>NUnit

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| 表达式 | 结果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 运行 `FullyQualifiedName` 包含 `Method` 的测试。 在 `vstest 15.1+` 中可用。 |
| `dotnet test --filter Name~TestMethod1` | 运行名称包含 `TestMethod1` 的测试。 |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | 运行属于类 `NUnitNamespace.UnitTest1` 的测试。<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | 运行除 `NUnitNamespace.UnitTest1.TestMethod1` 之外的其他所有测试。 |
| `dotnet test --filter TestCategory=CategoryA` | 运行含 `[Category("CategoryA")]` 批注的测试。 |
| `dotnet test --filter Priority=2` | 运行含 `[Priority(2)]` 批注的测试。<br>

**使用条件运算符 | 和 &amp;**

| 表达式 | 结果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | 运行 `FullyQualifiedName` 包含 `UnitTest1` 或 `TestCategory` 是 `CategoryA` 的测试  。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | 运行 `FullyQualifiedName` 包含 `UnitTest1` 且 `TestCategory` 是 `CategoryA` 的测试  。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 运行 `FullyQualifiedName` 包含 `UnitTest1` 且 `TestCategory` 是 `CategoryA` 或 `Priority` 是 1 的测试   。 |

有关详细信息，请参阅 [TestCase 筛选器](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)
