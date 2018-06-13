---
title: 正規表現の例
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee4d884a0efbeb6e57ed727396bf3bcb39979774
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172504"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="15d8a-102">正規表現の例</span><span class="sxs-lookup"><span data-stu-id="15d8a-102">Regular Expression Examples</span></span>
<span data-ttu-id="15d8a-103">このセクションでは、一般的なアプリケーションで正規表現を使用するときのコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d8a-104"><xref:System.Web.RegularExpressions> 名前空間には、正規表現オブジェクトがたくさん含まれています。このオブジェクトは、HTML、XML、ASP.NET 文書の文字列を解析する事前定義済み正規表現パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="15d8a-105">たとえば、<xref:System.Web.RegularExpressions.TagRegex> クラスは文字列の開始タグを識別します。<xref:System.Web.RegularExpressions.CommentRegex> クラスは文字列の ASP.NET コメントを識別します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15d8a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="15d8a-106">In This Section</span></span>  
 [<span data-ttu-id="15d8a-107">例: HREFS のスキャン</span><span class="sxs-lookup"><span data-stu-id="15d8a-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="15d8a-108">入力文字列を検索して、文字列内のすべての href="..." の値と位置を出力する例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="15d8a-109">例: 日付形式の変更</span><span class="sxs-lookup"><span data-stu-id="15d8a-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="15d8a-110">mm/dd/yy 形式の日付を dd-mm-yy 形式の日付に置換する例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="15d8a-111">方法: URL からプロトコルとポート番号を抽出する</span><span class="sxs-lookup"><span data-stu-id="15d8a-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="15d8a-112">URL を含む文字列からプロトコルとポート番号を抽出する例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="15d8a-113">たとえば、"http://www.contoso.com:8080/letters/readme.html" の場合は "http:8080" が返されます。</span><span class="sxs-lookup"><span data-stu-id="15d8a-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="15d8a-114">方法: 文字列から無効な文字を取り除く</span><span class="sxs-lookup"><span data-stu-id="15d8a-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="15d8a-115">文字列から無効な非英数文字を取り除く例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="15d8a-116">方法: 文字列が有効な電子メール形式であるかどうかを検証する</span><span class="sxs-lookup"><span data-stu-id="15d8a-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="15d8a-117">文字列が有効な電子メール形式であることを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15d8a-118">参照</span><span class="sxs-lookup"><span data-stu-id="15d8a-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="15d8a-119">.NET **System.Text.RegularExpressions** 名前空間のクラス ライブラリのリファレンス情報を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15d8a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="15d8a-120">Related Sections</span></span>  
 [<span data-ttu-id="15d8a-121">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="15d8a-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="15d8a-122">正規表現のプログラミング言語的な面の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="15d8a-123">正規表現のオブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="15d8a-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="15d8a-124">`System.Text.RegularExpression` 名前空間に含まれている正規表現クラスについて説明し、その使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="15d8a-125">正規表現の動作の詳細</span><span class="sxs-lookup"><span data-stu-id="15d8a-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="15d8a-126">.NET の正規表現の機能と動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="15d8a-127">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="15d8a-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="15d8a-128">正規表現を定義するために使う一連の文字、演算子、および構成体について説明します。</span><span class="sxs-lookup"><span data-stu-id="15d8a-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
