---
title: "方法: テキスト ファイルに書き込む (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="7a38b-102">方法: テキスト ファイルに書き込む (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7a38b-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="7a38b-103">テキストをファイルに書き込むさまざまな方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7a38b-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="7a38b-104">最初の 2 つの例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの静的なコンビニエンス メソッドを使用して、すべての IEnumerable\<string> の各要素と文字列をテキスト ファイルに記述しています。</span><span class="sxs-lookup"><span data-stu-id="7a38b-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="7a38b-105">例 3 は、ファイルに書き込むときに各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7a38b-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="7a38b-106">例 1 ～ 3 ではすべての既存の内容が上書きされます。例 4 に、既存のファイルにテキストを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7a38b-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="7a38b-107">これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a38b-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="7a38b-108">C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a38b-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a38b-109">例</span><span class="sxs-lookup"><span data-stu-id="7a38b-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="7a38b-110">これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a38b-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="7a38b-111">C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a38b-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7a38b-112">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="7a38b-112">Robust Programming</span></span>  
 <span data-ttu-id="7a38b-113">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a38b-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="7a38b-114">ファイルは存在するが、読み取り専用である。</span><span class="sxs-lookup"><span data-stu-id="7a38b-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="7a38b-115">パス名が長すぎる。</span><span class="sxs-lookup"><span data-stu-id="7a38b-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="7a38b-116">ディスクがいっぱいになっている。</span><span class="sxs-lookup"><span data-stu-id="7a38b-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a38b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a38b-117">See Also</span></span>  
 [<span data-ttu-id="7a38b-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7a38b-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7a38b-119">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7a38b-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="7a38b-120">サンプル: コレクションをアプリケーション ストレージに保存する</span><span class="sxs-lookup"><span data-stu-id="7a38b-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
