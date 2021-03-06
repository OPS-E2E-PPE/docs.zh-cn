---
title: 如何：连接到数据库
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 837919b1cfcdf46026ccfb37cbbec951c0ae41b8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634672"
---
# <a name="how-to-connect-to-a-database"></a>如何：连接到数据库
<xref:System.Data.Linq.DataContext> 是用来连接到数据库、从中检索对象以及将更改提交回数据库的主要渠道。 可以像使用 ADO.NET <xref:System.Data.SqlClient.SqlConnection>一样使用 <xref:System.Data.Linq.DataContext>。 事实上，<xref:System.Data.Linq.DataContext> 是用您提供的连接或连接字符串初始化的。 有关详细信息，请参阅[DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)。  
  
 <xref:System.Data.Linq.DataContext> 的用途是将您对对象的请求转换成要对数据库执行的 SQL 查询，然后将查询结果汇编成对象。 <xref:System.Data.Linq.DataContext> 通过实现与标准查询运算符（如 `Where` 和 `Select`）相同的运算符模式来实现语言集成查询（LINQ）。  
  
> [!IMPORTANT]
> 维护安全连接最为重要。 有关详细信息，请参阅[LINQ to SQL 中的安全性](security-in-linq-to-sql.md)。  
  
## <a name="example"></a>示例  
 在下面的示例中，使用 <xref:System.Data.Linq.DataContext> 连接到 Northwind 示例数据库并检索所在城市为伦敦的客户行。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 每个数据库表表示为一个可借助 `Table` 方法（通过使用实体类来标识它）使用的 <xref:System.Data.Linq.DataContext.GetTable%2A> 集合。  
  
## <a name="example"></a>示例  
 最佳的做法是声明一个强类型化的 <xref:System.Data.Linq.DataContext>，而不是依靠基本 <xref:System.Data.Linq.DataContext> 类和 <xref:System.Data.Linq.DataContext.GetTable%2A> 方法。 强类型化的 <xref:System.Data.Linq.DataContext> 将所有 `Table` 集合声明为上下文的成员，如下例中所示。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 然后您就可以更加简单地将对来自伦敦的客户的查询表达成：  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另请参阅

- [与数据库通信](communicating-with-the-database.md)
