---
title: "方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a><span data-ttu-id="d42b5-102">方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d42b5-102">How to: Convert RTF to Plain Text (C# Programming Guide)</span></span>
<span data-ttu-id="d42b5-103">リッチ テキスト形式 (RTF: Rich Text Format) は、1980 年代の後半にマイクロソフトが開発したドキュメント形式で、オペレーティング システム間でドキュメントを交換できます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-103">Rich Text Format (RTF) is a document format developed by Microsoft in the late 1980s to enable the exchange of documents across operating systems.</span></span> <span data-ttu-id="d42b5-104">RTF ドキュメントの読み取りと書き込みは、Microsoft Word と WordPad のどちらでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-104">Both Microsoft Word and WordPad can read and write RTF documents.</span></span> <span data-ttu-id="d42b5-105">.NET Framework では、<xref:System.Windows.Forms.RichTextBox> コントロールを使用して、RTF をサポートし、ユーザーが WYSIWIG 形式でテキストに書式設定を適用できるワード プロセッサを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-105">In the .NET Framework, you can use the <xref:System.Windows.Forms.RichTextBox> control to create a word processor that supports RTF and enables a user to apply formatting to text in a WYSIWIG manner.</span></span>  
  
 <span data-ttu-id="d42b5-106"><xref:System.Windows.Forms.RichTextBox> コントロールを使用して、プログラムによってドキュメントから RTF 書式指定コードを削除し、プレーンテキストに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-106">You can also use the <xref:System.Windows.Forms.RichTextBox> control to programmatically remove the RTF formatting codes from a document and convert it to plain text.</span></span> <span data-ttu-id="d42b5-107">このような操作は、Windows フォームにコントロールを埋め込まなくても実行できます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-107">You do not need to embed the control in a Windows Form to perform this kind of operation.</span></span>  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a><span data-ttu-id="d42b5-108">プロジェクトで RichTextBox コントロールを使用するには</span><span class="sxs-lookup"><span data-stu-id="d42b5-108">To use the RichTextBox control in a project</span></span>  
  
1.  <span data-ttu-id="d42b5-109">System.Windows.Forms.dll に対する参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d42b5-109">Add a reference to System.Windows.Forms.dll.</span></span>  
  
2.  <span data-ttu-id="d42b5-110">`System.Windows.Forms` 名前空間の using ディレクティブを追加します (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="d42b5-110">Add a using directive for the `System.Windows.Forms` namespace (optional).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d42b5-111">例</span><span class="sxs-lookup"><span data-stu-id="d42b5-111">Example</span></span>  
 <span data-ttu-id="d42b5-112">次の例では、サンプルの RTF ファイルをプレーンテキストに変換します。</span><span class="sxs-lookup"><span data-stu-id="d42b5-112">The following example converts a sample RTF file to plain text.</span></span> <span data-ttu-id="d42b5-113">ファイルは RTF 形式 (フォント情報など)、4 種類の Unicode 文字、および 4 個の拡張 ASCII 文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d42b5-113">The file contains RTF formatting (such as font information), four Unicode characters, and four extended ASCII characters.</span></span> <span data-ttu-id="d42b5-114">このコード例では、ファイルを開き、その内容を RTF として <xref:System.Windows.Forms.RichTextBox> に渡し、テキストとして取得して、<xref:System.Windows.Forms.MessageBox> に表示したうえで、UTF-8 形式のファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="d42b5-114">The example code opens the file, passes its content to a <xref:System.Windows.Forms.RichTextBox> as RTF, retrieves the content as text, displays the text in a <xref:System.Windows.Forms.MessageBox>, and outputs the text to a file in UTF-8 format.</span></span>  
  
 <span data-ttu-id="d42b5-115">`MessageBox` と出力ファイルには、次のテキストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d42b5-115">The `MessageBox` and the output file contain the following text:</span></span>  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 <span data-ttu-id="d42b5-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d42b5-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span></span>  
  
 <span data-ttu-id="d42b5-117">RTF 文字は 8 ビットでエンコードされますが、</span><span class="sxs-lookup"><span data-stu-id="d42b5-117">RTF characters are encoded in eight bits.</span></span> <span data-ttu-id="d42b5-118">ユーザーは、指定されたコード ページから、拡張 ASCII 文字のほか、Unicode 文字を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-118">However, users can specify Unicode characters in addition to extended ASCII characters from specified code pages.</span></span> <span data-ttu-id="d42b5-119"><xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> プロパティは [string](../../../csharp/language-reference/keywords/string.md) 型であるため、文字は Unicode UTF-16 としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-119">Because the <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> property is of type [string](../../../csharp/language-reference/keywords/string.md), the characters are encoded as Unicode UTF-16.</span></span> <span data-ttu-id="d42b5-120">ソース RTF ドキュメントの拡張 ASCII 文字と Unicode 文字は、テキスト出力で正しくエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="d42b5-120">Any extended ASCII characters and Unicode characters from the source RTF document are correctly encoded in the text output.</span></span>  
  
 <span data-ttu-id="d42b5-121"><xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> メソッドを使用してテキストをディスクに書き込むと、テキストは UTF-8 としてエンコードされます (バイト オーダー マークなし)。</span><span class="sxs-lookup"><span data-stu-id="d42b5-121">If you use the <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> method to write the text to disk, the text will be encoded as UTF-8 (without a Byte Order Mark).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42b5-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d42b5-122">See Also</span></span>  
 <span data-ttu-id="d42b5-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d42b5-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span></span>   
 [<span data-ttu-id="d42b5-124">文字列</span><span class="sxs-lookup"><span data-stu-id="d42b5-124">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

