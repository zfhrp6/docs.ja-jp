---
title: "方法 : 文字列が有効な電子メール形式であるかどうかを検証する"
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
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdbb64cac1f1d4043b8b935fcad32aec88b7bb7a
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="98091-102">方法 : 文字列が有効な電子メール形式であるかどうかを検証する</span><span class="sxs-lookup"><span data-stu-id="98091-102">How to: Verify that Strings Are in Valid Email Format</span></span>
<span data-ttu-id="98091-103">正規表現を使用して文字列の形式が有効な電子メール形式であるかどうかを検証する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98091-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98091-104">例</span><span class="sxs-lookup"><span data-stu-id="98091-104">Example</span></span>  
 <span data-ttu-id="98091-105">次の例では、 `IsValidEmail` メソッドを定義します。このメソッドは、文字列に有効な電子メール アドレスが含まれている場合に `true` を返し、含まれていない場合に `false` を返します。それ以外の動作は行いません。</span><span class="sxs-lookup"><span data-stu-id="98091-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>  
  
 <span data-ttu-id="98091-106">電子メール アドレスが有効であることを確認するため、`IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> メソッドを呼び出し、`(@)(.+)$` の正規表現パターンを指定して、電子メール アドレスからドメイン名を切り離します。</span><span class="sxs-lookup"><span data-stu-id="98091-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="98091-107">3 番目のパラメーターは、一致したテキストを操作また置換するメソッドを表す <xref:System.Text.RegularExpressions.MatchEvaluator> デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="98091-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="98091-108">正規表現パターンは次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="98091-108">The regular expression pattern is interpreted as follows.</span></span>  
  
|<span data-ttu-id="98091-109">パターン</span><span class="sxs-lookup"><span data-stu-id="98091-109">Pattern</span></span>|<span data-ttu-id="98091-110">説明</span><span class="sxs-lookup"><span data-stu-id="98091-110">Description</span></span>|  
|-------------|-----------------|  
|`(@)`|<span data-ttu-id="98091-111">@ 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-111">Match the @ character.</span></span> <span data-ttu-id="98091-112">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="98091-112">This is the first capturing group.</span></span>|  
|`(.+)`|<span data-ttu-id="98091-113">任意の文字の 1 回以上の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="98091-114">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="98091-114">This is the second capturing group.</span></span>|  
|`$`|<span data-ttu-id="98091-115">入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="98091-115">End the match at the end of the string.</span></span>|  
  
 <span data-ttu-id="98091-116">ドメイン名は @ 文字と合わせて `DomainMapper` メソッドに渡されます。このメソッドは <xref:System.Globalization.IdnMapping> クラスを使用して、US-ASCII 文字の範囲に含まれない Unicode 文字を Punycode に変換します。</span><span class="sxs-lookup"><span data-stu-id="98091-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="98091-117">また、このメソッドは、`invalid` メソッドがドメイン名に無効な文字を検出すると、`True` フラグを <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="98091-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="98091-118">このメソッドは、Punycode ドメイン名の前に @ 記号を付けて、これを `IsValidEmail` メソッドに返します。</span><span class="sxs-lookup"><span data-stu-id="98091-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>  
  
 <span data-ttu-id="98091-119">次に、`IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出して、電子メール アドレスが正規表現パターンに準拠するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="98091-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>  
  
 <span data-ttu-id="98091-120">`IsValidEmail` メソッドは、認証によって電子メール アドレスを検証するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="98091-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="98091-121">電子メール アドレスの形式として有効かどうかを判断しているだけです。</span><span class="sxs-lookup"><span data-stu-id="98091-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="98091-122">さらに、 `IsValidEmail` メソッドは、最上位ドメイン名が [IANA ルート ゾーン データベース](https://www.iana.org/domains/root/db)に掲載されている有効なドメイン名であることを確認しません (これには検索操作が必要です)。</span><span class="sxs-lookup"><span data-stu-id="98091-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="98091-123">代わりに、正規表現によって単に最上位ドメイン名が 2 ～ 24 文字の ASCII 英数字で構成されており、最初の文字と末尾の文字は英数字、その他の文字は英数字またはハイフン (-) であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="98091-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 <span data-ttu-id="98091-124">この例の正規表現パターン ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` の意味を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="98091-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following table.</span></span> <span data-ttu-id="98091-125">正規表現のコンパイルでは、<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> フラグが使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="98091-125">Note that the regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>  
  
|<span data-ttu-id="98091-126">パターン</span><span class="sxs-lookup"><span data-stu-id="98091-126">Pattern</span></span>|<span data-ttu-id="98091-127">説明</span><span class="sxs-lookup"><span data-stu-id="98091-127">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="98091-128">文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="98091-128">Begin the match at the start of the string.</span></span>|  
|`(?(")`|<span data-ttu-id="98091-129">最初の文字が引用符であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="98091-129">Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="98091-130">`(?(")` は代替構成体の開始位置です。</span><span class="sxs-lookup"><span data-stu-id="98091-130">`(?(")` is the beginning of an alternation construct.</span></span>|  
|`(?("")("".+?(?<!\\)""@)`|<span data-ttu-id="98091-131">最初の文字が引用符である場合、始まりの引用符に続く 1 つ以上の任意の文字と終わりの引用符に一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-131">If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="98091-132">終わりの引用符の前には円記号 (\\) を使用できません。</span><span class="sxs-lookup"><span data-stu-id="98091-132">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="98091-133">`(?<!` はゼロ幅の否定先読みアサーションの開始です。</span><span class="sxs-lookup"><span data-stu-id="98091-133">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="98091-134">文字列はアット マーク (@) で終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="98091-134">The string should conclude with an at sign (@).</span></span>|  
|`&#124;(([0-9a-z]`|<span data-ttu-id="98091-135">最初の文字が引用符でない場合は、a ～ z または A ～ Z の任意の英字または 0 ～ 9 の任意の数字と一致します (比較では大文字小文字は区別されません)。</span><span class="sxs-lookup"><span data-stu-id="98091-135">If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>|  
|`(\.(?!\.))`|<span data-ttu-id="98091-136">次の文字がピリオドの場合は、その文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-136">If the next character is a period, match it.</span></span> <span data-ttu-id="98091-137">ピリオドでない場合は、次の文字を先読みして照合を継続します。</span><span class="sxs-lookup"><span data-stu-id="98091-137">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="98091-138">`(?!\.)` は、2 つの連続するピリオドが電子メール アドレスのローカル部分に出現することを防ぐゼロ幅の負の先読みアサーションです。</span><span class="sxs-lookup"><span data-stu-id="98091-138">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>|  
|``&#124;[-!#\$%&'\*\+/=\?\^`{}\&#124;~\w]``|<span data-ttu-id="98091-139">次の文字がピリオドでない場合は、任意の単語文字または -!#$%'\*+=?^\`{}&#124;~ のいずれかの文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-139">If the next character is not a period, match any word character or one of the following characters: -!#$%'\*+=?^\`{}&#124;~.</span></span>|  
|``((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`{}\&#124;~\w])*``|<span data-ttu-id="98091-140">0 回以上の代替パターン (ピリオドとそれに続くピリオド以外の文字、または複数の文字のうちのいずれかの 1 文字) と一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-140">Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>|  
|`@`|<span data-ttu-id="98091-141">@ 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-141">Match the @ character.</span></span>|  
|`(?<=[0-9a-z])`|<span data-ttu-id="98091-142">@ 文字の前にくる文字が A ～ Z、a ～ z、または 0 ～ 9 である場合に照合を継続します。</span><span class="sxs-lookup"><span data-stu-id="98091-142">Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="98091-143">`(?<=[0-9a-z])` 構成体は、ゼロ幅の正の後読みアサーションを定義します。</span><span class="sxs-lookup"><span data-stu-id="98091-143">The `(?<=[0-9a-z])` construct defines a zero-width positive lookbehind assertion.</span></span>|  
|`(?(\[)`|<span data-ttu-id="98091-144">@ に続く文字が左角かっこかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="98091-144">Check whether the character that follows @ is an opening bracket.</span></span>|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|<span data-ttu-id="98091-145">左角かっこの場合は、左角かっこ、それに続く IP アドレス (各セットがピリオドで区切られた、4 セットの 1 ～ 3 桁の数字)、および右角かっこと一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-145">If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>|  
|`&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`|<span data-ttu-id="98091-146">@ に続く文字が左角かっこでない場合は、値が A - Z、a - z、または 0 - 9 の 1 つの英数字の後に、ハイフンの 0 回以上の出現、A - Z、a - z、または 0 - 9 の値の 0 個または 1 つの英数字、さらにピリオドが続くパターンと一致します。</span><span class="sxs-lookup"><span data-stu-id="98091-146">If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="98091-147">このパターンは 1 回以上繰り返すことができ、後ろに最上位ドメイン名が続く必要があります。</span><span class="sxs-lookup"><span data-stu-id="98091-147">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|<span data-ttu-id="98091-148">最上位ドメイン名では、最初の文字と最後の文字が英数字文字 (a ～ z、A ～ Z、0 ～ 9) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="98091-148">The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="98091-149">また、0 ～ 22 文字の ASCII 文字 (英数字またはハイフン) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="98091-149">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>|  
|`$`|<span data-ttu-id="98091-150">入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="98091-150">End the match at the end of the string.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="98091-151">電子メール アドレスの検証に正規表現を使用する代わりに、<xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="98091-151">Instead of using a regular expression to validate an email address, you can use the <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="98091-152">電子メール アドレスが有効であるかどうかを判別するには、電子メール アドレスを<xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> クラス コンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="98091-152">To determine whether an email address is valid, pass the email address to the <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> class constructor.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98091-153">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="98091-153">Compiling the Code</span></span>  
 <span data-ttu-id="98091-154">`IsValidEmail` メソッドと `DomainMapper` メソッドは、正規表現ユーティリティ メソッドのライブラリに含めることができるほか、アプリケーション クラス内のプライベートな静的メソッドやインスタンス メソッドとして含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="98091-154">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>  
  
 <span data-ttu-id="98091-155">これらを正規表現ライブラリに含めるには、Visual Studio のクラス ライブラリ プロジェクトにコードをコピーして貼り付けるか、コードをテキスト ファイルにコピーして貼り付けて、次のようなコマンドでコマンド ラインからコンパイルします (ソース コード ファイルの名前を RegexUtilities.cs または RegexUtilities.vb と仮定しています)。</span><span class="sxs-lookup"><span data-stu-id="98091-155">To include them in a regular expression library, either copy and paste the code into a Visual Studio Class Library project, or copy and paste it into a text file and compile it from the command line with a command like the following (assuming that the name of the source code file is RegexUtilities.cs or RegexUtilities.vb:</span></span>  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 <span data-ttu-id="98091-156">また、<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> メソッドを使用して、この正規表現を正規表現ライブラリに追加できます。</span><span class="sxs-lookup"><span data-stu-id="98091-156">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>  
  
 <span data-ttu-id="98091-157">正規表現ライブラリ内で使用した場合は、次のようなコードを使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="98091-157">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 <span data-ttu-id="98091-158">電子メール検証の正規表現を含む RegexUtilities.dll という名前のクラス ライブラリを作成してあると仮定した場合、この例は次の方法のいずれかでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="98091-158">Assuming you've created a class library named RegexUtilities.dll that includes your email validation regular expression, you can compile this example in either of the following ways:</span></span>  
  
-   <span data-ttu-id="98091-159">Visual Studio では、コンソール アプリケーションを作成して、RegexUtilities.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="98091-159">In Visual Studio, by creating a Console Application and adding a reference to RegexUtilities.dll to your project.</span></span>  
  
-   <span data-ttu-id="98091-160">コマンド ラインからは、ソース コードをテキスト ファイルにコピーして貼り付け、次のようなコマンドでコンパイルします (ソース コード ファイルの名前を Example.cs または Example.vb と仮定しています)。</span><span class="sxs-lookup"><span data-stu-id="98091-160">From the command line, by copying and pasting the source code into a text file and compiling it with a command like the following (assuming that the name of the source code file is Example.cs or Example.vb:</span></span>  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="98091-161">参照</span><span class="sxs-lookup"><span data-stu-id="98091-161">See Also</span></span>  
 [<span data-ttu-id="98091-162">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="98091-162">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
