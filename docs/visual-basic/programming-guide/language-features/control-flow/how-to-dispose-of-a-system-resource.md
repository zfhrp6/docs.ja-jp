---
title: '方法: システム リソースを破棄する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647232"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>方法: システム リソースを破棄する (Visual Basic)
使用することができます、`Using`システムは、コード ブロックを終了するときに、リソースの破棄を保証するためにブロックします。 これは、大量のメモリを消費する、またはその他のコンポーネントが使用する必要も、システム リソースを使用している場合に便利です。  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>コードの後に、データベース接続を破棄するには  
  
1.  必ず記録し、適切な[Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 、ソース ファイルの先頭にデータベース接続に (この場合、 <xref:System.Data.SqlClient>)。  
  
2.  作成、`Using`ブロックを`Using`と`End Using`ステートメントです。 ブロックの内部には、データベース接続を処理するコードを配置します。  
  
3.  接続を宣言し、そのインスタンスを作成の一部として、`Using`ステートメントです。  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     システムは、未処理の例外の大文字と小文字を含む、ブロックを終了する方法に関係なく、リソースを破棄します。  
  
     アクセスすることはできません注`sqc`から外、`Using`ブロック、そのスコープは、ブロックに制限されているためです。  
  
     ファイルのハンドルまたは COM ラッパーなどのシステム リソースでは、これと同じ手法を使用できます。 使用する、`Using`終了した後、その他のコンポーネントの使用可能なリソースのままにすることを確認する場合は、ブロック、`Using`ブロックします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.SqlClient.SqlConnection>  
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)
