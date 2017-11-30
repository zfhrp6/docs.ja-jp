---
title: "正規表現の例: HREFS のスキャン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="f37f5-102">正規表現の例: HREFS のスキャン</span><span class="sxs-lookup"><span data-stu-id="f37f5-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="f37f5-103">次の例では、入力文字列を検索して、文字列中のすべての href="…" 値とその場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="f37f5-104">Regex オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f37f5-104">The Regex Object</span></span>  
 <span data-ttu-id="f37f5-105">`DumpHRefs`メソッドは、ユーザー コードから複数回呼び出すことがあります、これを使用して、 `static` (`Shared` Visual Basic で)<xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f37f5-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f37f5-106">これにより、正規表現をキャッシュする正規表現エンジンを新しいのインスタンス化のオーバーヘッドを回避<xref:System.Text.RegularExpressions.Regex>オブジェクト、メソッドが呼び出されるたびにします。</span><span class="sxs-lookup"><span data-stu-id="f37f5-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="f37f5-107">A<xref:System.Text.RegularExpressions.Match>オブジェクトを文字列に一致するすべての反復処理に使用しています。</span><span class="sxs-lookup"><span data-stu-id="f37f5-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="f37f5-108">`DumpHRefs` メソッドを呼び出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="f37f5-109">この正規表現パターン `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="f37f5-110">パターン</span><span class="sxs-lookup"><span data-stu-id="f37f5-110">Pattern</span></span>|<span data-ttu-id="f37f5-111">説明</span><span class="sxs-lookup"><span data-stu-id="f37f5-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="f37f5-112">リテラル文字列 "href" と一致します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-112">Match the literal string "href".</span></span> <span data-ttu-id="f37f5-113">一致では、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="f37f5-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="f37f5-114">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="f37f5-115">等号と一致します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="f37f5-116">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-116">Match zero or more white-space characters.</span></span>|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|<span data-ttu-id="f37f5-117">キャプチャされたグループに、結果を割り当てずに、次のいずれかに一致します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-117">Match one of the following without assigning the result to a captured group:</span></span><br /><br /> <span data-ttu-id="f37f5-118">は、引用符または引用符または後に引用符またはアポストロフィ アポストロフィ以外の任意の文字の 0 個以上の出現が続くアポストロフィです。</span><span class="sxs-lookup"><span data-stu-id="f37f5-118">-   A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="f37f5-119">このパターンには `1` という名前のグループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f37f5-119">The group named `1` is included in this pattern.</span></span><br /><span data-ttu-id="f37f5-120">-1 つ以上の空白以外の文字。</span><span class="sxs-lookup"><span data-stu-id="f37f5-120">-   One or more non-white-space characters.</span></span> <span data-ttu-id="f37f5-121">このパターンには `1` という名前のグループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f37f5-121">The group named `1` is included in this pattern.</span></span>|  
|`(?<1>[^"']*)`|<span data-ttu-id="f37f5-122">引用符またはアポストロフィ以外の任意の文字の 0 回以上の繰り返しを `1` という名前のキャプチャ グループに代入します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`"(?<1>\S+)`|<span data-ttu-id="f37f5-123">1 個以上の空白以外の文字を `1` という名前のキャプチャ グループに代入します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="f37f5-124">Match 結果クラス</span><span class="sxs-lookup"><span data-stu-id="f37f5-124">Match Result Class</span></span>  
 <span data-ttu-id="f37f5-125">検索の結果が格納されている、<xref:System.Text.RegularExpressions.Match>検索で抽出されたすべての部分文字列へのアクセスを提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="f37f5-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="f37f5-126">情報も保存されて検索対象の文字列と正規表現が使用されているため、呼び出すことができます、<xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>から別の検索最後の 1 つの終了位置を実行するメソッド。</span><span class="sxs-lookup"><span data-stu-id="f37f5-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="f37f5-127">明示的に指定したキャプチャ</span><span class="sxs-lookup"><span data-stu-id="f37f5-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="f37f5-128">従来の正規表現では、キャプチャするかっこに自動的に連番が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f37f5-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="f37f5-129">その結果、2 つの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="f37f5-129">This leads to two problems.</span></span> <span data-ttu-id="f37f5-130">1 つ目の問題は、かっこのペアの挿入や削除を行って正規表現が修正されると、新しい番号を反映するために、番号付きのキャプチャを参照するコードをすべて書き直す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="f37f5-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="f37f5-131">2 つ目の問題は、ある文字列の検索用に 2 つの代替表現を指定する際、異なるかっこのペアを使用することが多いため、実際にどちらの代替表現から結果が返されたのかを判断するのが難しい場合があることです。</span><span class="sxs-lookup"><span data-stu-id="f37f5-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="f37f5-132">これらの問題に対処する、<xref:System.Text.RegularExpressions.Regex>クラスには、構文がサポートしている`(?<name>…)`指定されたスロットに一致するものをキャプチャするため (スロットの名前は、文字列または整数を使用して、整数をより迅速に取り消すことができる)。</span><span class="sxs-lookup"><span data-stu-id="f37f5-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="f37f5-133">これにより、同じ文字列に対する代替表現の一致結果をすべて同じ場所に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f37f5-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="f37f5-134">競合が発生する場合は、スロットにキャプチャされた最後の一致文字列が、適切な一致であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="f37f5-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="f37f5-135">(ただし、1 つのスロットで複数の一致文字列の完全なリストを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f37f5-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="f37f5-136">参照してください、<xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>詳細のコレクション)。</span><span class="sxs-lookup"><span data-stu-id="f37f5-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37f5-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f37f5-137">See Also</span></span>  
 [<span data-ttu-id="f37f5-138">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="f37f5-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
