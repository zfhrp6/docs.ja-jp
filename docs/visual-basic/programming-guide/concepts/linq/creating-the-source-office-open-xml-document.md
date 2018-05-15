---
title: ソース Office Open XML ドキュメント (Visual Basic) を作成します。
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 3db168b2c2971c3b44e54aefc24a9e08edb232d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="73ba0-102">ソース Office Open XML ドキュメント (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="73ba0-103">このトピックでは、このチュートリアルの他の例で使用する Office Open XML WordprocessingML ドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="73ba0-104">この手順に従うと、それぞれの例に記載されているとおりの出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="73ba0-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="73ba0-105">ただし、このチュートリアルの例では、任意の有効な WordprocessingML ドキュメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="73ba0-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="73ba0-106">このチュートリアルで使用するドキュメントを作成するには、Microsoft Office 2007 以降がインストールされているか、Microsoft Office 2003 と Word/Excel/PowerPoint 2007 ファイル形式用 Microsoft Office 互換機能パックを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="73ba0-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="73ba0-107">WordprocessingML ドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="73ba0-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="73ba0-108">WordprocessingML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="73ba0-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="73ba0-109">新しい Microsoft Word 文書を作成します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="73ba0-110">新しい文書に次のテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="73ba0-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="73ba0-111">"見出し 1" スタイルを使用して最初の行を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="73ba0-112">Visual Basic コードを含む行を選択します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="73ba0-113">最初の行は `Imports` キーワードで始まります。</span><span class="sxs-lookup"><span data-stu-id="73ba0-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="73ba0-114">最後の行は、「End クラス」です。</span><span class="sxs-lookup"><span data-stu-id="73ba0-114">The last line is "End Class".</span></span> <span data-ttu-id="73ba0-115">クーリエ フォントを使用してこれらの行を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-115">Format the lines with the courier font.</span></span> <span data-ttu-id="73ba0-116">これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="73ba0-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="73ba0-117">最後に、出力が含まれる行全体を選択し、`Code` スタイルを使用して書式設定します。</span><span class="sxs-lookup"><span data-stu-id="73ba0-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="73ba0-118">ドキュメントを保存し、SampleDoc.docx という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="73ba0-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73ba0-119">Microsoft Word 2003 を使用している場合、**[ファイルの種類]** ボックスの一覧の **[Word 2007 文書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73ba0-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ba0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="73ba0-120">See Also</span></span>  
 [<span data-ttu-id="73ba0-121">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="73ba0-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
