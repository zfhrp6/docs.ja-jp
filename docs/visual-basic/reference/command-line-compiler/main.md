---
title: "/main |Microsoft ドキュメント"
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: 61aa78e131ba8903035f630a540f49848f1acd3f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="main"></a><span data-ttu-id="f6802-102">/main</span><span class="sxs-lookup"><span data-stu-id="f6802-102">/main</span></span>
<span data-ttu-id="f6802-103">クラスまたはモジュールを含む指定、`Sub Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="f6802-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6802-104">構文</span><span class="sxs-lookup"><span data-stu-id="f6802-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6802-105">引数</span><span class="sxs-lookup"><span data-stu-id="f6802-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="f6802-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="f6802-106">Required.</span></span> <span data-ttu-id="f6802-107">クラスまたは含まれているモジュールに完全に修飾、`Sub Main`プログラムの開始時に呼び出されるプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="f6802-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="f6802-108">フォームの可能性があります**/main:module**または**/main:namespace.module**します。</span><span class="sxs-lookup"><span data-stu-id="f6802-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6802-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f6802-109">Remarks</span></span>  
 <span data-ttu-id="f6802-110">実行可能ファイルまたは Windows 実行可能プログラムを作成するときに、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6802-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="f6802-111">場合、 **/main**オプションを省略すると、コンパイラは有効な共有検索`Sub Main`のすべてのパブリック クラスおよびモジュールにします。</span><span class="sxs-lookup"><span data-stu-id="f6802-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="f6802-112">参照してください[Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)のさまざまな形式の詳細について、`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="f6802-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="f6802-113">`location`から継承するクラスは、 <xref:System.Windows.Forms.Form>、コンパイラは、既定値を用意`Main`クラスを持たない場合に、アプリケーションを開始するプロシージャ`Main`プロシージャ</xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="f6802-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="f6802-114">これにより、開発環境で作成されたコマンド ラインでコードをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="f6802-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 <span data-ttu-id="f6802-115">[!code-vb[VbVbalrCompiler&#16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6802-115">[!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span></span>  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f6802-116">統合開発環境 Visual Studio で/main を設定するには</span><span class="sxs-lookup"><span data-stu-id="f6802-116">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="f6802-117">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6802-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f6802-118">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="f6802-118">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="f6802-119">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6802-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="f6802-120">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6802-120">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="f6802-121">確認、**アプリケーション フレームワークを有効にする** チェック ボックスをオフになっています。</span><span class="sxs-lookup"><span data-stu-id="f6802-121">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="f6802-122">値を変更、**スタートアップ オブジェクト**ボックス。</span><span class="sxs-lookup"><span data-stu-id="f6802-122">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6802-123">例</span><span class="sxs-lookup"><span data-stu-id="f6802-123">Example</span></span>  
 <span data-ttu-id="f6802-124">次のコードのコンパイル`T2.vb`と`T3.vb`を指定している、`Sub Main`手順が記載されて、`Test2`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f6802-124">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6802-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6802-125">See Also</span></span>  
 <span data-ttu-id="f6802-126">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6802-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="f6802-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="f6802-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="f6802-128"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="f6802-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="f6802-129"> [NIB: Visual Basic バージョンこんにちは, World の](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span><span class="sxs-lookup"><span data-stu-id="f6802-129"> [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span></span>  
<span data-ttu-id="f6802-130"> [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="f6802-130"> [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span></span>
