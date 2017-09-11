---
title: "方法: テキスト ファイルに書き込む (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 12a74a5664a8f514c89d9de3ce470c98319f84d2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="bcdb8-102">方法: テキスト ファイルに書き込む (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bcdb8-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="bcdb8-103">テキストをファイルに書き込むさまざまな方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="bcdb8-104">最初の 2 つの例では、<xref:System.IO.File?displayProperty=fullName> クラスの静的なコンビニエンス メソッドを使用して、すべての IEnumerable\<string> の各要素と文字列をテキスト ファイルに記述しています。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=fullName> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="bcdb8-105">例 3 は、ファイルに書き込むときに各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="bcdb8-106">例 1 ～ 3 ではすべての既存の内容が上書きされます。例 4 に、既存のファイルにテキストを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="bcdb8-107">これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="bcdb8-108">C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdb8-109">例</span><span class="sxs-lookup"><span data-stu-id="bcdb8-109">Example</span></span>  
 <span data-ttu-id="bcdb8-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bcdb8-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span></span>  
  
 <span data-ttu-id="bcdb8-111">これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-111">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="bcdb8-112">C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-112">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bcdb8-113">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="bcdb8-113">Robust Programming</span></span>  
 <span data-ttu-id="bcdb8-114">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bcdb8-115">ファイルは存在するが、読み取り専用である。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-115">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="bcdb8-116">パス名が長すぎる。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-116">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="bcdb8-117">ディスクがいっぱいになっている。</span><span class="sxs-lookup"><span data-stu-id="bcdb8-117">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdb8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcdb8-118">See Also</span></span>  
 <span data-ttu-id="bcdb8-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb8-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bcdb8-120">[ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb8-120">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="bcdb8-121">サンプル: コレクションをアプリケーション ストレージに保存する</span><span class="sxs-lookup"><span data-stu-id="bcdb8-121">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)

