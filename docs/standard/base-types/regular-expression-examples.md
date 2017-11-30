---
title: "正規表現の例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d7fa8fe2bade9f20f71f846c717d79d6b6ffb36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="c13ec-102">正規表現の例</span><span class="sxs-lookup"><span data-stu-id="c13ec-102">Regular Expression Examples</span></span>
<span data-ttu-id="c13ec-103">このセクションでは、一般的なアプリケーションで正規表現を使用するときのコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c13ec-104"><xref:System.Web.RegularExpressions>名前空間には、HTML、XML、および ASP.NET のドキュメントから文字列を解析するための定義済みの正規表現パターンを実装する正規表現オブジェクトの数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c13ec-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="c13ec-105">たとえば、<xref:System.Web.RegularExpressions.TagRegex>クラスは、文字列の開始タグを識別し、<xref:System.Web.RegularExpressions.CommentRegex>クラスは、文字列内の ASP.NET のコメントを識別します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c13ec-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c13ec-106">In This Section</span></span>  
 [<span data-ttu-id="c13ec-107">例: HREFS のスキャン</span><span class="sxs-lookup"><span data-stu-id="c13ec-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="c13ec-108">入力文字列を検索し、すべての href を出力する例を紹介 =「...」の値と、文字列内の場所。</span><span class="sxs-lookup"><span data-stu-id="c13ec-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="c13ec-109">例: 日付形式の変更</span><span class="sxs-lookup"><span data-stu-id="c13ec-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="c13ec-110">形式 dd-月-年の日付のフォーム月/日/年の日付を置換する例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="c13ec-111">方法: URL からプロトコルとポート番号を抽出する</span><span class="sxs-lookup"><span data-stu-id="c13ec-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="c13ec-112">URL を含む文字列からプロトコルとポート番号を抽出する例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="c13ec-113">たとえば、"http://www.contoso.com:8080/letters/readme.html" の場合は "http:8080" が返されます。</span><span class="sxs-lookup"><span data-stu-id="c13ec-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="c13ec-114">方法: 文字列から無効な文字を取り除く</span><span class="sxs-lookup"><span data-stu-id="c13ec-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="c13ec-115">文字列から無効な英数字以外の文字を削除する例を提供します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="c13ec-116">方法: 文字列が有効な電子メール形式であるかどうかを検証する</span><span class="sxs-lookup"><span data-stu-id="c13ec-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="c13ec-117">使用できる文字列が有効な電子メール形式であることを確認する例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c13ec-118">参照</span><span class="sxs-lookup"><span data-stu-id="c13ec-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="c13ec-119">.Net クラス ライブラリ リファレンス情報を提供**System.Text.RegularExpressions**名前空間。</span><span class="sxs-lookup"><span data-stu-id="c13ec-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c13ec-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c13ec-120">Related Sections</span></span>  
 [<span data-ttu-id="c13ec-121">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="c13ec-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="c13ec-122">正規表現のプログラミング言語的な面の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="c13ec-123">正規表現のオブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="c13ec-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="c13ec-124">格納されている正規表現クラスについて説明します、`System.Text.RegularExpression`名前空間の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="c13ec-125">正規表現の動作の詳細</span><span class="sxs-lookup"><span data-stu-id="c13ec-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="c13ec-126">.NET の正規表現の動作と機能についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="c13ec-127">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="c13ec-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="c13ec-128">正規表現を定義するために使う一連の文字、演算子、および構成体について説明します。</span><span class="sxs-lookup"><span data-stu-id="c13ec-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
