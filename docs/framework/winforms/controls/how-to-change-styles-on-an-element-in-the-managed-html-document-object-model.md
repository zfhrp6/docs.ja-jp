---
title: '方法 : マネージ HTML DOM (Document Object Model) の要素のスタイルを変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 9ecb6b90508ca53e3801a633ac2444426e2f8113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531252"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="364e6-102">方法 : マネージ HTML DOM (Document Object Model) の要素のスタイルを変更する</span><span class="sxs-lookup"><span data-stu-id="364e6-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="364e6-103">Html 形式でスタイルを使用すると、ドキュメントとその要素の外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="364e6-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="364e6-104"><xref:System.Windows.Forms.HtmlDocument> および<xref:System.Windows.Forms.HtmlElement>サポート<xref:System.Windows.Forms.HtmlElement.Style%2A>次の形式のスタイルの文字列を使用するプロパティ。</span><span class="sxs-lookup"><span data-stu-id="364e6-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="364e6-105">ここでは、`DIV`フォントを太字で表示するには、Arial およびすべてのテキストに設定するスタイルの文字列で。</span><span class="sxs-lookup"><span data-stu-id="364e6-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="364e6-106">使用してスタイルを操作すると、問題、<xref:System.Windows.Forms.HtmlElement.Style%2A>プロパティが煩雑に追加し、文字列から個別のスタイル設定を削除することが検証されます。</span><span class="sxs-lookup"><span data-stu-id="364e6-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="364e6-107">たとえば、ユーザーが経由で、カーソルを移動するたびに斜体の以前のテキストをレンダリングするための複雑な手順はなります、 `DIV`、斜体、カーソルのままにするとオフを受け取ると、`DIV`です。</span><span class="sxs-lookup"><span data-stu-id="364e6-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="364e6-108">多数のこのようなスタイルを操作する必要がある場合は、時間を問題になります。</span><span class="sxs-lookup"><span data-stu-id="364e6-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="364e6-109">次の手順には、HTML ドキュメントと要素のスタイルを簡単に操作に使用できるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="364e6-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="364e6-110">プロシージャでは、新しいプロジェクトを作成し、コントロールをフォームに追加するなどの Windows フォームで基本的なタスクを実行する方法を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="364e6-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="364e6-111">Windows フォーム アプリケーションにおけるスタイルの変更を処理するには</span><span class="sxs-lookup"><span data-stu-id="364e6-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="364e6-112">新しい Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="364e6-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="364e6-113">末尾に使用するプログラミング言語の適切な拡張子の新しいクラス ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="364e6-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="364e6-114">コピー、`StyleGenerator`クラス ファイルに、このトピックの「例」でコード クラスし、、コードを保存します。</span><span class="sxs-lookup"><span data-stu-id="364e6-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="364e6-115">次の HTML を Test.htm をという名前のファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="364e6-115">Save the following HTML to a file named Test.htm.</span></span>  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  <span data-ttu-id="364e6-116">追加、<xref:System.Windows.Forms.WebBrowser>という名前のコントロール`webBrowser1`プロジェクトのメイン フォームにします。</span><span class="sxs-lookup"><span data-stu-id="364e6-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="364e6-117">プロジェクトのコード ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="364e6-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="364e6-118">いることを確認、`webBrowser1_DocumentCompleted`のリスナーとしてイベント ハンドラーが構成されている、<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>イベント。</span><span class="sxs-lookup"><span data-stu-id="364e6-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="364e6-119">Visual Studio でのダブルクリック、<xref:System.Windows.Forms.WebBrowser>制御以外の場合は、テキスト エディターで、リスナーをプログラムで構成します。</span><span class="sxs-lookup"><span data-stu-id="364e6-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="364e6-120">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="364e6-120">Run the project.</span></span> <span data-ttu-id="364e6-121">カーソルの最初の実行`DIV`コードの効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="364e6-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="364e6-122">例</span><span class="sxs-lookup"><span data-stu-id="364e6-122">Example</span></span>  
 <span data-ttu-id="364e6-123">次のコード例の完全なコードを示しています、`StyleGenerator`クラスは、既存のスタイル値を解析するをサポートします。 追加すると、変更すると、削除、スタイル、および要求された変更で新しいスタイルの値を返します。</span><span class="sxs-lookup"><span data-stu-id="364e6-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="364e6-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="364e6-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
