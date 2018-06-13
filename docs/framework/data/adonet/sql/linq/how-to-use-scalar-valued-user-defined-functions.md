---
title: '方法 : スカラー値のユーザー定義関数を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 3748f7b865de22353c8c0a91aaf52e672455ed38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355380"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>方法 : スカラー値のユーザー定義関数を使用する
<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性を使用することによって、クラスで定義されているクライアント メソッドを、ユーザー定義関数に対応付けることができます。 メソッドの本体は、メソッド呼び出しの目的を反映する式を構築し、変換および実行のためにその式を <xref:System.Data.Linq.DataContext> に渡します。  
  
> [!NOTE]
>  直接実行は、関数がクエリの外部で呼び出される場合のみ発生します。 詳細については、次を参照してください。[する方法: Call User-Defined 関数をインライン](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)です。  
  
## <a name="example"></a>例  
 次の SQL コードは、スカラー値のユーザー定義関数 `ReverseCustName()` を示しています。  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 このコードで、次のようなクライアント メソッドを対応付けます。  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 [ユーザー定義関数](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
