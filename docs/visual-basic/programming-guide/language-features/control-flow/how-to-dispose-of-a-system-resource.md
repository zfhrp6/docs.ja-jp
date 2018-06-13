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
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="b4710-102">方法: システム リソースを破棄する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4710-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="b4710-103">使用することができます、`Using`システムは、コード ブロックを終了するときに、リソースの破棄を保証するためにブロックします。</span><span class="sxs-lookup"><span data-stu-id="b4710-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="b4710-104">これは、大量のメモリを消費する、またはその他のコンポーネントが使用する必要も、システム リソースを使用している場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b4710-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="b4710-105">コードの後に、データベース接続を破棄するには</span><span class="sxs-lookup"><span data-stu-id="b4710-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="b4710-106">必ず記録し、適切な[Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 、ソース ファイルの先頭にデータベース接続に (この場合、 <xref:System.Data.SqlClient>)。</span><span class="sxs-lookup"><span data-stu-id="b4710-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="b4710-107">作成、`Using`ブロックを`Using`と`End Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b4710-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="b4710-108">ブロックの内部には、データベース接続を処理するコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="b4710-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="b4710-109">接続を宣言し、そのインスタンスを作成の一部として、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b4710-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="b4710-110">システムは、未処理の例外の大文字と小文字を含む、ブロックを終了する方法に関係なく、リソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b4710-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="b4710-111">アクセスすることはできません注`sqc`から外、`Using`ブロック、そのスコープは、ブロックに制限されているためです。</span><span class="sxs-lookup"><span data-stu-id="b4710-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="b4710-112">ファイルのハンドルまたは COM ラッパーなどのシステム リソースでは、これと同じ手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4710-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="b4710-113">使用する、`Using`終了した後、その他のコンポーネントの使用可能なリソースのままにすることを確認する場合は、ブロック、`Using`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="b4710-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4710-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4710-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="b4710-115">制御フロー</span><span class="sxs-lookup"><span data-stu-id="b4710-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="b4710-116">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="b4710-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="b4710-117">ループ構造</span><span class="sxs-lookup"><span data-stu-id="b4710-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="b4710-118">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="b4710-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="b4710-119">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="b4710-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="b4710-120">Using ステートメント</span><span class="sxs-lookup"><span data-stu-id="b4710-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
