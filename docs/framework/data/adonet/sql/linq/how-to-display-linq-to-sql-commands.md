---
title: '方法 : LINQ to SQL コマンドを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: 2be4096f03fe73f417b4b1871ebfc3b4f0f67206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359892"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="e5fa8-102">方法 : LINQ to SQL コマンドを表示する</span><span class="sxs-lookup"><span data-stu-id="e5fa8-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="e5fa8-103">SQL コマンドとその他の情報を表示するには、<xref:System.Data.Linq.DataContext.GetCommand%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5fa8-104">例</span><span class="sxs-lookup"><span data-stu-id="e5fa8-104">Example</span></span>  
 <span data-ttu-id="e5fa8-105">クエリからの出力、生成された SQL コマンド、コマンドの種類、および接続の種類をコンソール ウィンドウに表示する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="e5fa8-106">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-106">Output appears as follows:</span></span>  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5fa8-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5fa8-107">See Also</span></span>  
 [<span data-ttu-id="e5fa8-108">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="e5fa8-108">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
