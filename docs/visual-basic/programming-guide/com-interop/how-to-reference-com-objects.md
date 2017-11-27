---
title: "方法 : Visual Basic から COM オブジェクトを参照する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="d933d-102">方法 : Visual Basic から COM オブジェクトを参照する</span><span class="sxs-lookup"><span data-stu-id="d933d-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="d933d-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]、COM ライブラリの相互運用機能アセンブリの作成をタイプ ライブラリを持つ COM オブジェクトへの参照を追加することが必要です。</span><span class="sxs-lookup"><span data-stu-id="d933d-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="d933d-104">COM オブジェクトのメンバーへの参照は、相互運用機能アセンブリにルーティングされ、実際の COM オブジェクトに転送されます。</span><span class="sxs-lookup"><span data-stu-id="d933d-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="d933d-105">COM オブジェクトからの応答が相互運用機能アセンブリにルーティングされ、転送、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="d933d-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="d933d-106">.NET アセンブリで COM オブジェクトの型情報を埋め込むことで相互運用機能アセンブリを使用せず、COM オブジェクトを参照できます。</span><span class="sxs-lookup"><span data-stu-id="d933d-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="d933d-107">型情報を埋め込むには次のように設定します。、`Embed Interop Types`プロパティを`True`の COM オブジェクトへの参照。</span><span class="sxs-lookup"><span data-stu-id="d933d-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="d933d-108">コマンド ライン コンパイラを使用してコンパイルする場合を使用して、 `/link` COM ライブラリを参照するにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="d933d-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="d933d-109">詳細については、次を参照してください。 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)です。</span><span class="sxs-lookup"><span data-stu-id="d933d-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="d933d-110">統合開発環境 (IDE) から、タイプ ライブラリへの参照を追加するときに、相互運用機能アセンブリを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="d933d-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="d933d-111">コマンドラインからを使用する場合は、相互運用機能アセンブリを手動で作成する Tlbimp ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d933d-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="d933d-112">COM オブジェクトへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="d933d-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="d933d-113">**プロジェクト** メニューの 選択**参照の追加**をクリックし、 **COM**  ダイアログ ボックスのタブです。</span><span class="sxs-lookup"><span data-stu-id="d933d-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="d933d-114">COM オブジェクトの一覧から使用するコンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="d933d-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="d933d-115">相互運用機能アセンブリへのアクセスを簡素化するには追加、`Imports`クラスまたは COM オブジェクトを使用するモジュールの先頭にステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d933d-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="d933d-116">たとえば、次のコード例は名前空間をインポート`INKEDLib`で参照されるオブジェクトの`Microsoft InkEdit Control 1.0`ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="d933d-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="d933d-117">Tlbimp を使用して相互運用機能アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="d933d-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="d933d-118">なっていない、検索パスの一部と、現在では、ディレクトリが配置されている場合は、検索パスに Tlbimp の場所を追加します。</span><span class="sxs-lookup"><span data-stu-id="d933d-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="d933d-119">コマンド プロンプトから、次の情報を提供するには、Tlbimp を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d933d-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="d933d-120">タイプ ライブラリを含んでいる DLL の名前と場所</span><span class="sxs-lookup"><span data-stu-id="d933d-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="d933d-121">名前と場所、名前空間情報を格納する場所</span><span class="sxs-lookup"><span data-stu-id="d933d-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="d933d-122">ターゲットの相互運用機能アセンブリの名前と場所</span><span class="sxs-lookup"><span data-stu-id="d933d-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="d933d-123">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="d933d-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="d933d-124">Tlbimp を使用すると、未登録の COM オブジェクトであっても、タイプ ライブラリの相互運用機能アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d933d-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="d933d-125">しかし、ここで使用するのには、コンピューター上相互運用機能アセンブリによって参照される COM オブジェクトを正しく登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d933d-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="d933d-126">COM オブジェクトを登録するには、Windows オペレーティング システムに含まれている、Regsvr32 ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d933d-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d933d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d933d-127">See Also</span></span>  
 [<span data-ttu-id="d933d-128">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="d933d-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="d933d-129">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="d933d-129">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [<span data-ttu-id="d933d-130">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="d933d-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="d933d-131">チュートリアル : COM オブジェクトによる継承の実装</span><span class="sxs-lookup"><span data-stu-id="d933d-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="d933d-132">相互運用性のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d933d-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="d933d-133">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="d933d-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
