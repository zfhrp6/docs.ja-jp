---
title: "方法: Visual Basic から COM オブジェクトを参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f7f1112161d9be995cc80378ad9dd95c522198d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="700aa-102">方法 : Visual Basic から COM オブジェクトを参照する</span><span class="sxs-lookup"><span data-stu-id="700aa-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="700aa-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、COM ライブラリを相互運用機能アセンブリの作成をタイプ ライブラリを持つ COM オブジェクトへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="700aa-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="700aa-104">COM オブジェクトのメンバーへの参照は相互運用機能アセンブリにルーティングされ、実際の COM オブジェクトに転送されます。</span><span class="sxs-lookup"><span data-stu-id="700aa-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="700aa-105">COM オブジェクトからの応答が相互運用機能アセンブリにルーティングされ、転送、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="700aa-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span>  
  
 <span data-ttu-id="700aa-106">.NET アセンブリで COM オブジェクトの型情報を埋め込むことで相互運用機能アセンブリを使用せず、COM オブジェクトを参照できます。</span><span class="sxs-lookup"><span data-stu-id="700aa-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="700aa-107">型情報を埋め込むには次のように設定します。、`Embed Interop Types`プロパティを`True`の COM オブジェクトへの参照。</span><span class="sxs-lookup"><span data-stu-id="700aa-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="700aa-108">コマンド ライン コンパイラを使用してコンパイルする場合に使用して、 `/link` COM ライブラリを参照するにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="700aa-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="700aa-109">詳細については、次を参照してください。 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)します。</span><span class="sxs-lookup"><span data-stu-id="700aa-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="700aa-110">統合開発環境 (IDE) からタイプ ライブラリへの参照を追加するときに、相互運用機能アセンブリを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="700aa-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="700aa-111">をコマンドラインから使用する場合は、相互運用機能アセンブリを手動で作成する Tlbimp ユーティリティを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="700aa-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="700aa-112">COM オブジェクトへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="700aa-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="700aa-113">**プロジェクト** メニューの 選択**参照の追加** をクリックし、 **COM**  ダイアログ ボックスのタブです。</span><span class="sxs-lookup"><span data-stu-id="700aa-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="700aa-114">COM オブジェクトの一覧から使用するコンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="700aa-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="700aa-115">相互運用機能アセンブリへのアクセスを簡略化を追加、`Imports`ステートメントをクラスや COM オブジェクトを使用するモジュールの上部にします。</span><span class="sxs-lookup"><span data-stu-id="700aa-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="700aa-116">たとえば、次のコード例は名前空間をインポート`INKEDLib`で参照されるオブジェクトについて、`Microsoft InkEdit Control 1.0`ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="700aa-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     <span data-ttu-id="700aa-117">[!code-vb[VbVbalrInterop #&40;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="700aa-117">[!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span></span>  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="700aa-118">Tlbimp を使用して相互運用機能アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="700aa-118">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="700aa-119">なっていない検索パスの一部していない現在配置されているディレクトリの場合は、検索パスに Tlbimp の場所を追加します。</span><span class="sxs-lookup"><span data-stu-id="700aa-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="700aa-120">コマンド プロンプトで次の情報を提供するには、Tlbimp を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="700aa-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="700aa-121">タイプ ライブラリを含んでいる DLL の名前と場所</span><span class="sxs-lookup"><span data-stu-id="700aa-121">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="700aa-122">名前と場所、名前空間情報を保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="700aa-122">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="700aa-123">ターゲットの相互運用機能アセンブリの名前と場所</span><span class="sxs-lookup"><span data-stu-id="700aa-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="700aa-124">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="700aa-124">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="700aa-125">Tlbimp を使用すると、相互運用機能アセンブリの登録されていない COM オブジェクトにも、タイプ ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="700aa-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="700aa-126">ただし、ここで使用するのには、コンピューターの相互運用機能アセンブリで参照される COM オブジェクトを正しく登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="700aa-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="700aa-127">Windows オペレーティング システムに含まれている Regsvr32 ユーティリティを使用して COM オブジェクトを登録することができます。</span><span class="sxs-lookup"><span data-stu-id="700aa-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700aa-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="700aa-128">See Also</span></span>  
 <span data-ttu-id="700aa-129">[COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="700aa-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="700aa-130"> [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="700aa-130"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="700aa-131"> [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="700aa-131"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="700aa-132"> [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="700aa-132"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="700aa-133"> [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="700aa-133"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="700aa-134"> [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="700aa-134"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
