---
title: "文字列を使用するためのベスト プラクティス"
description: "文字列を使用するためのベスト プラクティス"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
ms.translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e
ms.contentlocale: ja-jp
ms.lasthandoff: 11/05/2016

---

# <a name="best-practices-for-using-strings"></a><span data-ttu-id="343c4-104">文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="343c4-104">Best practices for using strings</span></span>

<span data-ttu-id="343c4-105">.NET には、ローカライズされたアプリケーションやグローバル化されたアプリケーションを開発するための広範なサポートが用意されており、文字列の並べ替えや表示などの一般的な操作を実行するときに、現在のカルチャの規則や特定のカルチャの規則を簡単に適用できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="343c4-105">.NET provides extensive support for developing localized and globalized applications, and makes it easy to apply the conventions of either the current culture or a specific culture when performing common operations such as sorting and displaying strings.</span></span> <span data-ttu-id="343c4-106">しかし、文字列の並べ替えや比較の操作は、必ずしもカルチャに依存するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="343c4-106">But sorting or comparing strings is not always a culture-sensitive operation.</span></span> <span data-ttu-id="343c4-107">たとえば、アプリケーションが内部で使用する文字列は、通常、すべてのカルチャで同じように処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-107">For example, strings that are used internally by an application typically should be handled identically across all cultures.</span></span> <span data-ttu-id="343c4-108">XML タグ、HTML タグ、ユーザー名、ファイル パス、システム オブジェクトの名前などのカルチャに依存しない文字列データがカルチャに依存するかのように解釈されると、アプリケーション コードで軽度のバグが発生したり、パフォーマンスが低下したり、場合によってはセキュリティの問題を引き起こしたりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-108">When culturally independent string data, such as XML tags, HTML tags, user names, file paths, and the names of system objects, are interpreted as if they were culture-sensitive, application code can be subject to subtle bugs, poor performance, and, in some cases, security issues.</span></span>

<span data-ttu-id="343c4-109">ここでは、.NET の文字列の並べ替え、比較、および大文字と小文字の区別のメソッドについて検討し、適切な文字列処理メソッドを選択するための推奨事項と、文字列処理メソッドに関する追加情報を紹介します。</span><span class="sxs-lookup"><span data-stu-id="343c4-109">This article examines the string sorting, comparison, and casing methods in .NET, presents recommendations for selecting an appropriate string-handling method, and provides additional information about string-handling methods.</span></span> <span data-ttu-id="343c4-110">また、数値データ、日時データなど、書式付きデータを表示および格納のために処理する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="343c4-110">It also examines how formatted data, such as numeric data and date and time data, is handled for display and for storage.</span></span> 

<span data-ttu-id="343c4-111">この記事は、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="343c4-111">This article contains the following sections:</span></span>

* [<span data-ttu-id="343c4-112">文字列の使用に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="343c4-112">Recommendations for string usage</span></span>](#recommendations-for-string-usage)

* [<span data-ttu-id="343c4-113">文字列比較の明示的な指定</span><span class="sxs-lookup"><span data-stu-id="343c4-113">Specifying string comparisons explicitly</span></span>](#specifying-string-comparisons-explicitly)

* [<span data-ttu-id="343c4-114">文字列比較の詳細</span><span class="sxs-lookup"><span data-stu-id="343c4-114">The details of string comparison</span></span>](#the-details-of-string-comparison)

* [<span data-ttu-id="343c4-115">メソッド呼び出しに使用する StringComparison メンバーの選択</span><span class="sxs-lookup"><span data-stu-id="343c4-115">Choosing a StringComparison member for your method call</span></span>](#choosing-a-stringcomparison-member-for-your-method-call)

* [<span data-ttu-id="343c4-116">一般的な文字列比較メソッド</span><span class="sxs-lookup"><span data-stu-id="343c4-116">Common string comparison methods</span></span>](#common-string-comparison-methods)

* [<span data-ttu-id="343c4-117">間接的に文字列比較を実行するメソッド</span><span class="sxs-lookup"><span data-stu-id="343c4-117">Methods that perform string comparison indirectly</span></span>](#methods-that-perform-string-comparison-indirectly)

* [<span data-ttu-id="343c4-118">書式設定されたデータを表示および保持する</span><span class="sxs-lookup"><span data-stu-id="343c4-118">Displaying and persisting formatted data</span></span>](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a><span data-ttu-id="343c4-119">文字列の使用に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="343c4-119">Recommendations for string usage</span></span>

<span data-ttu-id="343c4-120">.NET による開発で文字列を使用するときの簡単な推奨事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-120">When you develop with .NET, follow these simple recommendations when you use strings:</span></span> 

* <span data-ttu-id="343c4-121">文字列操作に対して文字列比較の規則を明示的に指定するオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-121">Use overloads that explicitly specify the string comparison rules for string operations.</span></span> <span data-ttu-id="343c4-122">そのためには、通常、[StringComparison](xref:System.StringComparison) 型のパラメーターを持つメソッド オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="343c4-122">Typically, this involves calling a method overload that has a parameter of type [StringComparison](xref:System.StringComparison).</span></span>

* <span data-ttu-id="343c4-123">カルチャに依存しない文字列照合の安全な既定の方法として、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) を使用して比較を行います。</span><span class="sxs-lookup"><span data-stu-id="343c4-123">Use [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for comparisons as your safe default for culture-agnostic string matching.</span></span>

* <span data-ttu-id="343c4-124">パフォーマンスを向上させるには、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) による比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-124">Use comparisons with [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for better performance.</span></span>

* <span data-ttu-id="343c4-125">ユーザーに出力を表示する場合は、[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) に基づく文字列操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-125">Use string operations that are based on [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) when you display output to the user.</span></span>

* <span data-ttu-id="343c4-126">比較が言語的な意味を持たない場合 (記号としての比較など) は、[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) に基づく文字列操作ではなく、非言語的な [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 値または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-126">Use the non-linguistic [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) values instead of string operations based on [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) when the comparison is linguistically irrelevant (symbolic, for example).</span></span>

* <span data-ttu-id="343c4-127">比較のために文字列を正規化する場合は、[String.ToLowerInvariant](xref:System.String.ToLowerInvariant) メソッドではなく [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-127">Use the [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) method instead of the [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) method when you normalize strings for comparison.</span></span>

* <span data-ttu-id="343c4-128">2 つの文字列が等価かどうかをテストするには、[String](xref:System.String) `Equals` メソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-128">Use an overload of the [String](xref:System.String) `Equals` method to test whether two strings are equal.</span></span>

* <span data-ttu-id="343c4-129">[String](xref:System.String) `Compare` メソッドと [String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドのオーバーロードは、文字列を並べ替える場合に使用し、文字列の等価性を確認する場合には使用しません。</span><span class="sxs-lookup"><span data-stu-id="343c4-129">Use an overload of the [String](xref:System.String) `Compare` and [String.CompareTo](xref:System.String.CompareTo(System.String)) methods to sort strings, not to check for equality.</span></span>

* <span data-ttu-id="343c4-130">数値、日付など、文字列以外のデータをユーザー インターフェイスに表示するには、カルチャに依存する書式設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-130">Use culture-sensitive formatting to display non-string data, such as numbers and dates, in a user interface.</span></span> <span data-ttu-id="343c4-131">文字列以外のデータを文字列形式で保持するには、インバリアント カルチャを使用する書式設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-131">Use formatting with the invariant culture to persist non-string data in string form.</span></span>

<span data-ttu-id="343c4-132">文字列を使用する際に避ける必要があることを次に示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-132">Avoid the following practices when you use strings:</span></span>

* <span data-ttu-id="343c4-133">文字列操作に対して文字列比較の規則を明示的または暗黙的に指定しないオーバーロードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="343c4-133">Do not use overloads that do not explicitly or implicitly specify the string comparison rules for string operations.</span></span> 

* <span data-ttu-id="343c4-134">2 つの文字列が等価かどうかを確認する場合に、[String](xref:System.String) `Compare` メソッドまたは [String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドのオーバーロードで戻り値が 0 かどうかをテストする方法は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="343c4-134">Do not use an overload of the [String](xref:System.String) `Compare` or [String.CompareTo](xref:System.String.CompareTo(System.String)) methods and test for a return value of zero to determine whether two strings are equal.</span></span>

* <span data-ttu-id="343c4-135">数値データや日時データを文字列形式で保持する場合は、カルチャに依存する書式設定を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="343c4-135">Do not use culture-sensitive formatting to persist numeric data or date and time data in string form.</span></span>

## <a name="specifying-string-comparisons-explicitly"></a><span data-ttu-id="343c4-136">文字列比較の明示的な指定</span><span class="sxs-lookup"><span data-stu-id="343c4-136">Specifying string comparisons explicitly</span></span>

<span data-ttu-id="343c4-137">.NET の文字列操作メソッドは、ほとんどがオーバーロードされています。</span><span class="sxs-lookup"><span data-stu-id="343c4-137">Most of the string manipulation methods in .NET are overloaded.</span></span> <span data-ttu-id="343c4-138">通常は、既定の設定をそのまま使用する 1 つまたは複数のオーバーロードと、既定の設定を使用せずに文字列の比較または操作の正確な方法を定義するその他のオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="343c4-138">Typically, one or more overloads accept default settings, whereas others accept no defaults and instead define the precise way in which strings are to be compared or manipulated.</span></span> <span data-ttu-id="343c4-139">既定の設定に依存しないメソッドには、ほとんどの場合、[StringComparison](xref:System.StringComparison) 型のパラメーターが含まれています。これは、カルチャおよび大文字と小文字の区別によって文字列比較の規則を明示的に指定する列挙型です。</span><span class="sxs-lookup"><span data-stu-id="343c4-139">Most of the methods that do not rely on defaults include a parameter of type [StringComparison](xref:System.StringComparison), which is an enumeration that explicitly specifies rules for string comparison by culture and case.</span></span> <span data-ttu-id="343c4-140">[StringComparison](xref:System.StringComparison) 列挙型のメンバーを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-140">The following table describes the [StringComparison](xref:System.StringComparison) enumeration members.</span></span> 

<span data-ttu-id="343c4-141">StringComparison のメンバー</span><span class="sxs-lookup"><span data-stu-id="343c4-141">StringComparison member</span></span> | <span data-ttu-id="343c4-142">説明</span><span class="sxs-lookup"><span data-stu-id="343c4-142">Description</span></span>
----------------------- | -----------
[<span data-ttu-id="343c4-143">StringComparison.CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="343c4-143">StringComparison.CurrentCulture</span></span>](xref:System.StringComparison.CurrentCulture) | <span data-ttu-id="343c4-144">現在のカルチャを使用して、大文字と小文字を区別する比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-144">Performs a case-sensitive comparison using the current culture.</span></span>
[<span data-ttu-id="343c4-145">CurrentCultureIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="343c4-145">CurrentCultureIgnoreCase</span></span>](xref:System.StringComparison.CurrentCultureIgnoreCase) | <span data-ttu-id="343c4-146">現在のカルチャを使用して、大文字と小文字を区別しない比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-146">Performs a case-insensitive comparison using the current culture.</span></span>
[<span data-ttu-id="343c4-147">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="343c4-147">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal) | <span data-ttu-id="343c4-148">序数に基づく比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-148">Performs an ordinal comparison.</span></span>
[<span data-ttu-id="343c4-149">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="343c4-149">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase) | <span data-ttu-id="343c4-150">大文字と小文字を区別しない、序数に基づく比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-150">Performs a case-insensitive ordinal comparison.</span></span>

<span data-ttu-id="343c4-151">たとえば、文字または文字列に一致する[String](xref:System.String) オブジェクト内の部分文字列のインデックスを返す [String](xref:System.String) `IndexOf` メソッドには、次の 9 つのオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="343c4-151">For example, the [String](xref:System.String) `IndexOf` method, which returns the index of a substring in a [String](xref:System.String) object that matches either a character or a string, has nine overloads:</span></span>

* <span data-ttu-id="343c4-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char))、[IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32))、および [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32))。文字列内の文字の序数に基づく (大文字と小文字を区別し、カルチャに依存しない) 検索を既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)), and [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), which by default perform an ordinal (case-sensitive and culture-insensitive) search for a character in the string.</span></span>

* <span data-ttu-id="343c4-153">[IndexOf(String)](xref:System.String.IndexOf(System.String))、[IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32))、および [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32))。文字列内の部分文字列の、大文字と小文字を区別し、カルチャに依存した検索を既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-153">[IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)), and [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), which by default perform a case-sensitive and culture-sensitive search for a substring in the string.</span></span>

* <span data-ttu-id="343c4-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison))、[IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison))、および [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison))。比較の形式を指定できる StringComparison 型のパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="343c4-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)), and [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), which include a parameter of type StringComparison that allows the form of the comparison to be specified.</span></span>

<span data-ttu-id="343c4-155">次のような理由から、既定値を使用しないオーバーロードを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="343c4-155">We recommend that you select an overload that does not use default values, for the following reasons:</span></span>

* <span data-ttu-id="343c4-156">既定のパラメーターを持つオーバーロードには、序数に基づく比較を実行するもの (文字列インスタンスで [Char](xref:System.Char) を検索するもの) と、カルチャに依存するもの (文字列インスタンスで文字列を検索するもの) があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-156">Some overloads with default parameters (those that search for a [Char](xref:System.Char) in the string instance) perform an ordinal comparison, whereas others (those that search for a string in the string instance) are culture-sensitive.</span></span> <span data-ttu-id="343c4-157">どのメソッドがどの既定値を使用するのかを覚えておくのは容易ではなく、使用するオーバーロードを間違えやすくなります。</span><span class="sxs-lookup"><span data-stu-id="343c4-157">It is difficult to remember which method uses which default value, and easy to confuse the overloads.</span></span>

* <span data-ttu-id="343c4-158">メソッド呼び出しで既定値に依存するコードは、意図が不明確になります。</span><span class="sxs-lookup"><span data-stu-id="343c4-158">The intent of the code that relies on default values for method calls is not clear.</span></span> <span data-ttu-id="343c4-159">たとえば、既定値に依存する次の例では、2 つの文字列の序数に基づく比較と言語に基づく比較のどちらを開発者が意図しているのかや、`protocol` と "http" の大文字と小文字が違っていた場合に等価性テストで `false` が返されるのかどうかがわかりにくくなっています。</span><span class="sxs-lookup"><span data-stu-id="343c4-159">In the following example, which relies on defaults, it is difficult to know whether the developer actually intended an ordinal or a linguistic comparison of two strings, or whether a case difference between `protocol` and "http" might cause the test for equality to return `false`.</span></span>

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

<span data-ttu-id="343c4-160">一般的には、既定値に依存しないメソッドを呼び出すことをお勧めします。そうすると、コードの意図が明確になります。</span><span class="sxs-lookup"><span data-stu-id="343c4-160">In general, we recommend that you call a method that does not rely on defaults, because it makes the intent of the code unambiguous.</span></span> <span data-ttu-id="343c4-161">その結果、コードが読みやすくなるため、デバッグや保守も容易になります。</span><span class="sxs-lookup"><span data-stu-id="343c4-161">This, in turn, makes the code more readable and easier to debug and maintain.</span></span> <span data-ttu-id="343c4-162">次の例では、前の例で発生した問題に対応します。</span><span class="sxs-lookup"><span data-stu-id="343c4-162">The following example addresses the questions raised about the previous example.</span></span> <span data-ttu-id="343c4-163">序数比較を使用することと、大文字と小文字の違いを無視することを指定します。</span><span class="sxs-lookup"><span data-stu-id="343c4-163">It makes it clear that ordinal comparison is used and that differences in case are ignored.</span></span> 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a><span data-ttu-id="343c4-164">文字列比較の詳細</span><span class="sxs-lookup"><span data-stu-id="343c4-164">The details of string comparison</span></span>

<span data-ttu-id="343c4-165">文字列比較は、多くの文字列関連操作 (特に並べ替えおよび等価性テスト) の中核です。</span><span class="sxs-lookup"><span data-stu-id="343c4-165">String comparison is the heart of many string-related operations, particularly sorting and testing for equality.</span></span> <span data-ttu-id="343c4-166">文字列は、決まった順序で並べられています。たとえば、文字列の並べ替え済みリストで "my" が "string" の前にある場合は、比較で "my" が "string" 以下になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-166">Strings sort in a determined order: If "my" appears before "string" in a sorted list of strings, "my" must compare less than or equal to "string".</span></span> <span data-ttu-id="343c4-167">また、比較は等価性を暗黙的に定義します。</span><span class="sxs-lookup"><span data-stu-id="343c4-167">Additionally, comparison implicitly defines equality.</span></span> <span data-ttu-id="343c4-168">比較演算では、等価と見なされた文字列に対して 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-168">The comparison operation returns zero for strings it deems equal.</span></span> <span data-ttu-id="343c4-169">これは、どちらの文字列ももう一方の文字列より小さくないという意味に解釈するとわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="343c4-169">A good interpretation is that neither string is less than the other.</span></span> <span data-ttu-id="343c4-170">文字列に関係する、意味のある操作のほとんどには、他の文字列との比較か、正しく定義された並べ替え操作の実行のいずれかまたは両方の処理が含まれています。</span><span class="sxs-lookup"><span data-stu-id="343c4-170">Most meaningful operations involving strings include one or both of these procedures: comparing with another string, and executing a well-defined sort operation.</span></span>

<span data-ttu-id="343c4-171">しかし、2 つの文字列の等価性や並べ替え順序を評価する場合、正しい結果は 1 つではありません。結果は、文字列の比較に使用される基準に依存するためです。</span><span class="sxs-lookup"><span data-stu-id="343c4-171">However, evaluating two strings for equality or sort order does not yield a single, correct result; the outcome depends on the criteria used to compare the strings.</span></span> <span data-ttu-id="343c4-172">特に、序数に基づく文字列比較や、現在のカルチャまたはインバリアント カルチャ (英語をベースとする、ロケールに依存しないカルチャ) の大文字と小文字の規則や並べ替えの規則に基づく文字列比較では、さまざまな結果が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-172">In particular, string comparisons that are ordinal or that are based on the casing and sorting conventions of the current culture or the invariant culture (a locale-agnostic culture based on the English language) may produce different results.</span></span>

### <a name="string-comparisons-that-use-the-current-culture"></a><span data-ttu-id="343c4-173">現在のカルチャを使用する文字列比較</span><span class="sxs-lookup"><span data-stu-id="343c4-173">String comparisons that use the current culture</span></span>

<span data-ttu-id="343c4-174">文字列を比較するときの基準として現在のカルチャの規則が使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-174">One criterion involves using the conventions of the current culture when comparing strings.</span></span> <span data-ttu-id="343c4-175">現在のカルチャに基づく比較では、スレッドの現在のカルチャ (ロケール) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-175">Comparisons that are based on the current culture use the thread's current culture or locale.</span></span> <span data-ttu-id="343c4-176">言語的な意味を持つデータや、カルチャに依存したユーザー操作を反映するデータに対しては、常に現在のカルチャに基づく比較を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-176">You should always use comparisons that are based on the current culture when data is linguistically relevant, and when it reflects culture-sensitive user interaction.</span></span> 

<span data-ttu-id="343c4-177">しかし、.NET の比較や大文字と小文字の区別の動作は、カルチャによって変わります。</span><span class="sxs-lookup"><span data-stu-id="343c4-177">However, comparison and casing behavior in .NET changes when the culture changes.</span></span> <span data-ttu-id="343c4-178">たとえば、開発されたコンピューターとは異なるカルチャのコンピューターでアプリケーションが実行された場合や、実行中のスレッドのカルチャが変更された場合などに、この変化が生じます。</span><span class="sxs-lookup"><span data-stu-id="343c4-178">This happens when an application executes on a computer that has a different culture than the computer on which the application was developed, or when the executing thread changes its culture.</span></span> <span data-ttu-id="343c4-179">これは意図的な動作ですが、多くの開発者にはまだあまり知られていません。</span><span class="sxs-lookup"><span data-stu-id="343c4-179">This behavior is intentional, but it remains non-obvious to many developers.</span></span> <span data-ttu-id="343c4-180">次の例は、英語 (米国) ("en-US") とスウェーデン語 ("sv-SE") のカルチャの並べ替え順序の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-180">The following example illustrates differences in sort order between the U.S. English ("en-US") and Swedish ("sv-SE") cultures.</span></span> <span data-ttu-id="343c4-181">並べ替えられた文字列配列で、"ångström"、"Windows"、および "Visual Studio" の位置が違っていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="343c4-181">Note that the words "ångström", "Windows", and "Visual Studio" appear in different positions in the sorted string arrays.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

<span data-ttu-id="343c4-182">現在のカルチャを使用する、大文字と小文字を区別しない比較は、スレッドの現在のカルチャの大文字と小文字の区別の規則が無視される以外は、カルチャに依存した比較と同じです。</span><span class="sxs-lookup"><span data-stu-id="343c4-182">Case-insensitive comparisons that use the current culture are the same as culture-sensitive comparisons, except that they ignore case as dictated by the thread's current culture.</span></span> <span data-ttu-id="343c4-183">この動作も、並べ替え順序に影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-183">This behavior may manifest itself in sort orders as well.</span></span> 

<span data-ttu-id="343c4-184">現在のカルチャのセマンティクスを使用する比較は、次のメソッドで既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-184">Comparisons that use current culture semantics are the default for the following methods:</span></span>

* <span data-ttu-id="343c4-185">[StringComparison](xref:System.StringComparison) パラメーターを含まない [String](xref:System.String) `Compare` オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="343c4-185">[String](xref:System.String) `Compare` overloads that do not include a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="343c4-186">[String.CompareTo](xref:System.String.CompareTo(System.String)) オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="343c4-186">[String.CompareTo](xref:System.String.CompareTo(System.String)) overloads.</span></span>

* <span data-ttu-id="343c4-187">既定の [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) メソッド。</span><span class="sxs-lookup"><span data-stu-id="343c4-187">The default [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) method.</span></span> 

* <span data-ttu-id="343c4-188">既定の [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) メソッド。</span><span class="sxs-lookup"><span data-stu-id="343c4-188">The default [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) method.</span></span>

* <span data-ttu-id="343c4-189">検索パラメーターとして [String](xref:System.String) を受け取る、[StringComparison](xref:System.StringComparison) パラメーターを持たない [String](xref:System.String) `IndexOf` のオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="343c4-189">[String](xref:System.String) `IndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="343c4-190">検索パラメーターとして [String](xref:System.String) を受け取る、[StringComparison](xref:System.StringComparison) パラメーターを持たない [String](xref:System.String) `LastIndexOf` のオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="343c4-190">[String](xref:System.String) `LastIndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

<span data-ttu-id="343c4-191">どのような場合でも、[StringComparison](xref:System.StringComparison) パラメーターを持つオーバーロードを呼び出して、メソッド呼び出しの意図を明確にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="343c4-191">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter to make the intent of the method call clear.</span></span> 

<span data-ttu-id="343c4-192">非言語的な文字列データが言語的に解釈されたり、特定のカルチャの文字列データが別のカルチャの規則で解釈されたりすると、軽度のバグやあまり軽度でないバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-192">Subtle and not so subtle bugs can emerge when non-linguistic string data is interpreted linguistically, or when string data from a particular culture is interpreted using the conventions of another culture.</span></span> <span data-ttu-id="343c4-193">その典型的な例が、トルコ語の I の問題です。</span><span class="sxs-lookup"><span data-stu-id="343c4-193">The canonical example is the Turkish-I problem.</span></span>

<span data-ttu-id="343c4-194">英語 (米国) を含むほぼすべてのラテン アルファベットでは、文字 "i" (\u0069) は "I" (\u0049) の小文字版です。</span><span class="sxs-lookup"><span data-stu-id="343c4-194">For nearly all Latin alphabets, including U.S. English, the character "i" (\u0069) is the lowercase version of the character "I" (\u0049).</span></span> <span data-ttu-id="343c4-195">この大文字と小文字の規則は、このようなカルチャでプログラミングを行う人にとってはすぐに当たり前のことになります。</span><span class="sxs-lookup"><span data-stu-id="343c4-195">This casing rule quickly becomes the default for someone programming in such a culture.</span></span> <span data-ttu-id="343c4-196">しかし、トルコ語 ("tr-TR") のアルファベットには、"i" の大文字版である "ドット付きの I" ("İ" (\u0130)) や、</span><span class="sxs-lookup"><span data-stu-id="343c4-196">However, the Turkish ("tr-TR") alphabet includes an "I with a dot" character "İ" (\u0130), which is the capital version of "i".</span></span> <span data-ttu-id="343c4-197">大文字にすると "I" になる小文字の "ドットなしの i" ("ı" (\u0131)) があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-197">Turkish also includes a lowercase "i without a dot" character, "ı" (\u0131), which capitalizes to "I".</span></span> <span data-ttu-id="343c4-198">この動作は、アゼルバイジャン語 ("az") のカルチャでも発生します。</span><span class="sxs-lookup"><span data-stu-id="343c4-198">This behavior occurs in the Azerbaijani ("az") culture as well.</span></span>

<span data-ttu-id="343c4-199">したがって、"i" を大文字にしたり "I" を小文字にしたりする動作に関する前提は、すべてのカルチャで有効なわけではありません。</span><span class="sxs-lookup"><span data-stu-id="343c4-199">Therefore, assumptions made about capitalizing "i" or lowercasing "I" are not valid among all cultures.</span></span> <span data-ttu-id="343c4-200">文字列比較ルーチンの既定のオーバーロードを使用すると、カルチャ間の差異の影響を受けることになります。</span><span class="sxs-lookup"><span data-stu-id="343c4-200">If you use the default overloads for string comparison routines, they will be subject to variance between cultures.</span></span> <span data-ttu-id="343c4-201">また、非言語的なデータを比較する場合も、既定のオーバーロードを使用すると望ましくない結果が返される可能性があります。たとえば次の例では、文字列 "file" と "FILE" の大文字と小文字を区別しない比較を実行しようとしています。</span><span class="sxs-lookup"><span data-stu-id="343c4-201">If the data to be compared is non-linguistic, using the default overloads can produce undesirable results, as the following attempt to perform a case-insensitive comparison of the strings "file" and "FILE" illustrates.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

<span data-ttu-id="343c4-202">この比較は、セキュリティが重要となる状況でカルチャが不注意に使用されると、重大な問題を引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-202">This comparison could cause significant problems if the culture is inadvertently used in security-sensitive settings, as in the following example.</span></span> <span data-ttu-id="343c4-203">`IsFileURI("file:")` などのメソッド呼び出しは、現在のカルチャが英語 (米国) の場合は `true` を返しますが、現在のカルチャがトルコ語の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="343c4-203">A method call such as `IsFileURI("file:")` returns `true` if the current culture is U.S. English, but `false` if the current culture is Turkish.</span></span> <span data-ttu-id="343c4-204">したがって、"FILE:" で始まる URI へのアクセスを大文字と小文字の区別なくブロックするセキュリティ対策は、トルコ語のシステムでは攻略される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-204">Thus, on Turkish systems, someone could circumvent security measures that block access to case-insensitive URIs that begin with "FILE:".</span></span>

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

<span data-ttu-id="343c4-205">この例の "file:" は、カルチャに依存しない非言語的な識別子として解釈されるものなので、コードを次のように書き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-205">In this case, because "file:" is meant to be interpreted as a non-linguistic, culture-insensitive identifier, the code should instead be written as shown in the following example.</span></span>

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a><span data-ttu-id="343c4-206">序数に基づく文字列操作</span><span class="sxs-lookup"><span data-stu-id="343c4-206">Ordinal String Operations</span></span>

<span data-ttu-id="343c4-207">メソッド呼び出しで [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 値または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 値を指定すると、非言語的な比較が行われ、自然言語の特性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-207">Specifying the [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) value in a method call signifies a non-linguistic comparison in which the features of natural languages are ignored.</span></span> <span data-ttu-id="343c4-208">これらの [StringComparison](xref:System.StringComparison) 値を使用して呼び出されたメソッドでは、文字列操作の判断が、大文字と小文字の指定、またはカルチャでパラメーター化される同等の表ではなく、単純なバイト比較に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="343c4-208">Methods that are invoked with these [StringComparison](xref:System.StringComparison) values base string operation decisions on simple byte comparisons instead of casing or equivalence tables that are parameterized by culture.</span></span> <span data-ttu-id="343c4-209">これにより、ほとんどの場合に文字列が意図されたとおりに解釈され、コードの実行速度と信頼性も向上します。</span><span class="sxs-lookup"><span data-stu-id="343c4-209">In most cases, this approach best fits the intended interpretation of strings while making code faster and more reliable.</span></span> 

<span data-ttu-id="343c4-210">序数に基づく比較とは、各文字列の各バイトが言語的に解釈されずに比較される文字列比較です (たとえば、"windows" と "Windows" は一致しません)。</span><span class="sxs-lookup"><span data-stu-id="343c4-210">Ordinal comparisons are string comparisons in which each byte of each string is compared without linguistic interpretation; for example, "windows" does not match "Windows".</span></span> <span data-ttu-id="343c4-211">文字列が厳密に一致する必要がある状況や、慎重な照合ポリシーが求められる状況では、この比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-211">Use this comparison when the context dictates that strings should be matched exactly or demands conservative matching policy.</span></span> <span data-ttu-id="343c4-212">また、序数に基づく比較は最も高速な比較演算でもあります。これは、結果を判定するときに言語の規則が適用されないためです。</span><span class="sxs-lookup"><span data-stu-id="343c4-212">Additionally, ordinal comparison is the fastest comparison operation because it applies no linguistic rules when determining a result.</span></span>

<span data-ttu-id="343c4-213">.NET の文字列には、null 文字が埋め込まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-213">Strings in .NET can contain embedded null characters.</span></span> <span data-ttu-id="343c4-214">序数に基づく比較とカルチャに依存した比較 (インバリアント カルチャを使用する比較を含む) の最も明白な違いの 1 つは、文字列に埋め込まれた null 文字の処理に関連しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-214">One of the clearest differences between ordinal and culture-sensitive comparison (including comparisons that use the invariant culture) concerns the handling of embedded null characters in a string.</span></span> <span data-ttu-id="343c4-215">これらの文字は、[String](xref:System.String) `Compare` メソッドや [String](xref:System.String) `Equals` メソッドを使用して、カルチャに依存した比較 (インバリアント カルチャを使用する比較を含む) を実行する場合には無視されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-215">These characters are ignored when you use the [String](xref:System.String) `Compare` and [String](xref:System.String) `Equals` methods to perform culture-sensitive comparisons (including comparisons that use the invariant culture).</span></span> <span data-ttu-id="343c4-216">その結果、カルチャに依存した比較では、null 文字が埋め込まれた文字列と null 文字が埋め込まれていない文字列が等価と見なされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-216">As a result, in culture-sensitive comparisons, strings that contain embedded null characters can be considered equal to strings that do not.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="343c4-217">埋め込まれた null 文字は、文字列比較メソッドでは無視されますが、文字列検索メソッド ([String.Contains](xref:System.String.Contains(System.String))、[String.EndsWith](xref:System.String.EndsWith(System.String))、[String.IndexOf](xref:System.String.IndexOf(System.Char))、[String.LastIndexOf](xref:System.String.LastIndexOf(System.String))、[String.StartsWith](xref:System.String.StartsWith(System.String)) など) では無視されません。</span><span class="sxs-lookup"><span data-stu-id="343c4-217">Although string comparison methods disregard embedded null characters, string search methods such as [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)), and [String.StartsWith](xref:System.String.StartsWith(System.String)) do not.</span></span> 

<span data-ttu-id="343c4-218">次の例では、文字列 "Aa" と、"A" と "a" の間にいくつかの null 文字が埋め込まれた類似の文字列とのカルチャに依存した比較を実行して、2 つの文字列が等価と見なされることを示しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-218">The following example performs a culture-sensitive comparison of the string "Aa" with a similar string that contains several embedded null characters between "A" and "a", and shows how the two strings are considered equal.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

<span data-ttu-id="343c4-219">一方、次の例のように序数に基づく比較を使用すると、これらの文字列は等価とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="343c4-219">However, the strings are not considered equal when you use ordinal comparison, as the following example shows.</span></span>

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

<span data-ttu-id="343c4-220">序数に基づく比較の次に慎重な方法は、大文字と小文字を区別しない序数に基づく比較です。</span><span class="sxs-lookup"><span data-stu-id="343c4-220">Case-insensitive ordinal comparisons are the next most conservative approach.</span></span> <span data-ttu-id="343c4-221">この比較では、大文字と小文字の区別のほとんどが無視されます (たとえば、"windows" と "Windows" は一致します)。</span><span class="sxs-lookup"><span data-stu-id="343c4-221">These comparisons ignore most casing; for example, "windows" matches "Windows".</span></span> <span data-ttu-id="343c4-222">ASCII 文字を操作する場合、このポリシーは [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) と同等ですが、通常の ASCII の大文字と小文字の区別が無視されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-222">When dealing with ASCII characters, this policy is equivalent to [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), except that it ignores the usual ASCII casing.</span></span> <span data-ttu-id="343c4-223">したがって、[A, Z] (\u0041-\u005A) の任意の文字が [a,z] (\u0061-\007A) の対応する文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="343c4-223">Therefore, any character in [A, Z] (\u0041-\u005A) matches the corresponding character in [a,z] (\u0061-\007A).</span></span> <span data-ttu-id="343c4-224">ASCII の範囲外の大文字と小文字の区別には、インバリアント カルチャのテーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-224">Casing outside the ASCII range uses the invariant culture's tables.</span></span> <span data-ttu-id="343c4-225">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-225">Therefore, the following comparison:</span></span>

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

<span data-ttu-id="343c4-226">この比較は、次の比較と同等です (ただし、より高速です)。</span><span class="sxs-lookup"><span data-stu-id="343c4-226">is equivalent to (but faster than) this comparison:</span></span> 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

<span data-ttu-id="343c4-227">とはいえ、これらの比較はどちらも非常に高速です。</span><span class="sxs-lookup"><span data-stu-id="343c4-227">These comparisons are still very fast.</span></span>

<span data-ttu-id="343c4-228">[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) と [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) は、どちらもバイナリ値を直接使用するため、照合に最適です。</span><span class="sxs-lookup"><span data-stu-id="343c4-228">Both [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) and [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) use the binary values directly, and are best suited for matching.</span></span> <span data-ttu-id="343c4-229">比較の設定について確信を持てない場合は、この 2 つのいずれかの値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="343c4-229">When you are not sure about your comparison settings, use one of these two values.</span></span> <span data-ttu-id="343c4-230">ただし、これらの値を使用するとバイトごとの比較が行われるため、言語的な順序 (英語の辞書のような順序) ではなくバイナリの順序で並べ替えが行われます。</span><span class="sxs-lookup"><span data-stu-id="343c4-230">However, because they perform a byte-by-byte comparison, they do not sort by a linguistic sort order (like an English dictionary) but by a binary sort order.</span></span> <span data-ttu-id="343c4-231">したがって、結果をユーザーに表示すると、ほとんどの場合不自然に見えます。</span><span class="sxs-lookup"><span data-stu-id="343c4-231">The results may look odd in most contexts if displayed to users.</span></span>

<span data-ttu-id="343c4-232">序数に基づくセマンティクスは、[StringComparison](xref:System.StringComparison) 引数を含まない [String](xref:System.String) `Equals` のオーバーロード (等値演算子を含む) で既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-232">Ordinal semantics are the default for [String](xref:System.String) `Equals` overloads that do not include a [StringComparison](xref:System.StringComparison) argument (including the equality operator).</span></span> <span data-ttu-id="343c4-233">どのような場合でも、[StringComparison](xref:System.StringComparison) パラメーターを持つオーバーロードを呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="343c4-233">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter.</span></span>

### <a name="string-operations-that-use-the-invariant-culture"></a><span data-ttu-id="343c4-234">インバリアント カルチャを使用する文字列操作</span><span class="sxs-lookup"><span data-stu-id="343c4-234">String operations that use the invariant culture</span></span>

<span data-ttu-id="343c4-235">インバリアント カルチャを使用する比較では、静的 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティから返される [CompareInfo](xref:System.Globalization.CompareInfo) プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-235">Comparisons with the invariant culture use the [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="343c4-236">この動作は、すべてのシステムで同じです。範囲外の文字は、等価のインバリアント文字と見なされる文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-236">This behavior is the same on all systems; it translates any characters outside its range into what it believes are equivalent invariant characters.</span></span> <span data-ttu-id="343c4-237">このポリシーは、同じ文字列動作のセットを複数のカルチャにわたって保持する場合に便利ですが、予期しない結果になることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="343c4-237">This policy can be useful for maintaining one set of string behavior across cultures, but it often provides unexpected results.</span></span>

<span data-ttu-id="343c4-238">インバリアント カルチャを使用する、大文字と小文字を区別しない比較でも、静的 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティから返される静的 [CompareInfo](xref:System.Globalization.CompareInfo) プロパティが比較情報として使用されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-238">Case-insensitive comparisons with the invariant culture use the static [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property for comparison information as well.</span></span> <span data-ttu-id="343c4-239">変換後の文字の大文字と小文字の違いは無視されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-239">Any case differences among these translated characters are ignored.</span></span>

<span data-ttu-id="343c4-240">[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) オブジェクトによって、[String](xref:System.String) `Compare` メソッドで特定の文字のセットが等価と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-240">The [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) object makes a [String](xref:System.String) `Compare` method interpret certain sets of characters as equivalent.</span></span> <span data-ttu-id="343c4-241">たとえば、次の例が等価になるのは、インバリアント カルチャでは妥当です。</span><span class="sxs-lookup"><span data-stu-id="343c4-241">For example, the following equivalence is valid under the invariant culture:</span></span>

<span data-ttu-id="343c4-242">InvariantCulture: a + ̊ = å</span><span class="sxs-lookup"><span data-stu-id="343c4-242">InvariantCulture: a + ̊ = å</span></span>

<span data-ttu-id="343c4-243">latin small lette A 文字 "a" (\u0061) は、combining ring above 文字 "+ " ̊" (\u030a) の横にある場合、latin small letter A with ring above 文字 "å" (\u00e5) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-243">The latin small lette A character "a" (\u0061), when it is next to the combining ring above character "+ " ̊" (\u030a), is interpreted as the latin small letter A with ring above character "å" (\u00e5).</span></span> <span data-ttu-id="343c4-244">この動作は、次の例に示すように、序数に基づく比較とは異なります。</span><span class="sxs-lookup"><span data-stu-id="343c4-244">As the following example shows, this behavior differs from ordinal comparison.</span></span>

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

<span data-ttu-id="343c4-245">ファイル名やクッキーなど、"å" のような組み合わせが出現する可能性がある要素を解釈する場合にも、序数に基づく比較を使用するのが最も明確かつ適切な方法になります。</span><span class="sxs-lookup"><span data-stu-id="343c4-245">When interpreting file names, cookies, or anything else where a combination such as "å" can appear, ordinal comparisons still offer the most transparent and fitting behavior.</span></span>

<span data-ttu-id="343c4-246">結局のところ、インバリアント カルチャには、比較に使用する際に便利なプロパティがほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="343c4-246">On balance, the invariant culture has very few properties that make it useful for comparison.</span></span> <span data-ttu-id="343c4-247">インバリアント カルチャを使用すると、言語的な意味を持つ形で比較が行われるため、記号の完全な等価性は保証されません。その一方で、特定のカルチャでの表示にも適していません。</span><span class="sxs-lookup"><span data-stu-id="343c4-247">It does comparison in a linguistically relevant manner, which prevents it from guaranteeing full symbolic equivalence, but it is not the choice for display in any culture.</span></span> <span data-ttu-id="343c4-248">たとえば、表示する並べ替え済みの識別子のリストを含む大きなデータ ファイルがアプリケーションに付属している場合に、そのリストにエントリを追加するには、インバリアント スタイルの並べ替えを使用する挿入が必要になります。</span><span class="sxs-lookup"><span data-stu-id="343c4-248">For example, if a large data file that contains a list of sorted identifiers for display accompanies an application, adding to this list would require an insertion with invariant-style sorting.</span></span>

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a><span data-ttu-id="343c4-249">メソッド呼び出しに使用する StringComparison メンバーの選択</span><span class="sxs-lookup"><span data-stu-id="343c4-249">Choosing a StringComparison member for your method call</span></span>

<span data-ttu-id="343c4-250">文字列のセマンティックなコンテキストと [StringComparison](xref:System.StringComparison) 列挙型のメンバーとの対応関係の概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-250">The following table outlines the mapping from semantic string context to a [StringComparison](xref:System.StringComparison) enumeration member.</span></span>

<span data-ttu-id="343c4-251">データ</span><span class="sxs-lookup"><span data-stu-id="343c4-251">Data</span></span> | <span data-ttu-id="343c4-252">動作</span><span class="sxs-lookup"><span data-stu-id="343c4-252">Behavior</span></span> | <span data-ttu-id="343c4-253">対応する System.StringComparison 値</span><span class="sxs-lookup"><span data-stu-id="343c4-253">Corresponding System.StringComparison value</span></span>
---- | -------- | -------------------------------------------
<span data-ttu-id="343c4-254">大文字と小文字が区別される内部識別子、XML や HTTP などの標準の、大文字と小文字が区別される識別子、または大文字と小文字が区別されるセキュリティ関連の設定。</span><span class="sxs-lookup"><span data-stu-id="343c4-254">Case-sensitive internal identifiers, case-sensitive identifiers in standards such as XML and HTTP, or case-sensitive security-related settings.</span></span> | <span data-ttu-id="343c4-255">バイトが正確に一致する非言語的識別子。</span><span class="sxs-lookup"><span data-stu-id="343c4-255">A non-linguistic identifier, where bytes match exactly.</span></span> | [<span data-ttu-id="343c4-256">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="343c4-256">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal)
<span data-ttu-id="343c4-257">大文字と小文字が区別されない内部識別子、XML や HTTP などの標準の、大文字と小文字が区別される識別子、ファイル パス、レジストリ キーと値、環境変数、リソース識別子 (ハンドル名など)、または大文字と小文字が区別されないセキュリティ関連の設定。</span><span class="sxs-lookup"><span data-stu-id="343c4-257">Case-insensitive internal identifiers, case-insensitive identifiers in standards such as XML and HTTP, file paths, registry keys and values, environment variables, resource identifiers (for example, handle names), or case-insensitive security-related settings.</span></span> | <span data-ttu-id="343c4-258">大文字と小文字の区別に関係ない非言語的識別子。</span><span class="sxs-lookup"><span data-stu-id="343c4-258">A non-linguistic identifier, where case is irrelevant.</span></span> | [<span data-ttu-id="343c4-259">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="343c4-259">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase)
<span data-ttu-id="343c4-260">ユーザーに表示されるデータまたはほとんどのユーザーの入力。</span><span class="sxs-lookup"><span data-stu-id="343c4-260">Data displayed to the user or most user input.</span></span> | <span data-ttu-id="343c4-261">特定の言語の規則を必要とするデータ。</span><span class="sxs-lookup"><span data-stu-id="343c4-261">Data that requires local linguistic customs.</span></span> | <span data-ttu-id="343c4-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) または [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span><span class="sxs-lookup"><span data-stu-id="343c4-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) or [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span></span>

## <a name="common-string-comparison-methods"></a><span data-ttu-id="343c4-263">一般的な文字列比較メソッド</span><span class="sxs-lookup"><span data-stu-id="343c4-263">Common string comparison methods</span></span>

<span data-ttu-id="343c4-264">以降では、文字列比較でよく使用されるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="343c4-264">The following sections describe the methods that are most commonly used for string comparison.</span></span>

### <a name="stringcompare"></a><span data-ttu-id="343c4-265">String.Compare</span><span class="sxs-lookup"><span data-stu-id="343c4-265">String.Compare</span></span>

<span data-ttu-id="343c4-266">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-266">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-267">このメソッドは文字列解釈の中心的な操作となるため、メソッド呼び出しのすべてのインスタンスを調べて、文字列を現在のカルチャに従って解釈するべきか、カルチャから切り離して (記号として) 扱うべきかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-267">As the operation most central to string interpretation, all instances of these method calls should be examined to determine whether strings should be interpreted according to the current culture, or dissociated from the culture (symbolically).</span></span> <span data-ttu-id="343c4-268">ほとんどは後者であるため、その場合は代わりに [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) の比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-268">Typically, it is the latter, and a [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) comparison should be used instead.</span></span>

<span data-ttu-id="343c4-269">[CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) プロパティから返される [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) クラスにも、[CompareOptions](xref:System.Globalization.CompareOptions) フラグ列挙体でさまざまな照合方法 (序数に基づく、空白文字を無視する、カナ型を無視するなど) を指定できる [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="343c4-269">The [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) class, which is returned by the [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) property, also includes a [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) method that provides a large number of matching options (ordinal, ignoring white space, ignoring kana type, and so on) by means of the [CompareOptions](xref:System.Globalization.CompareOptions) flag enumeration.</span></span> 

### <a name="stringcompareto"></a><span data-ttu-id="343c4-270">String.CompareTo</span><span class="sxs-lookup"><span data-stu-id="343c4-270">String.CompareTo</span></span>

<span data-ttu-id="343c4-271">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-271">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-272">このメソッドには、現時点では、[StringComparison](xref:System.StringComparison) 型を指定するオーバーロードはありません。</span><span class="sxs-lookup"><span data-stu-id="343c4-272">This method does not currently offer an overload that specifies a [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="343c4-273">通常は、このメソッドを推奨される [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) の形式に変換できます。</span><span class="sxs-lookup"><span data-stu-id="343c4-273">It is usually possible to convert this method to the recommended [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) form.</span></span>

<span data-ttu-id="343c4-274">このメソッドは、[IComparable](xref:System.IComparable) インターフェイスと [IComparable&lt;T&gt;](xref:System.IComparable%601) インターフェイスを実装する型に実装されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-274">Types that implement the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces implement this method.</span></span> <span data-ttu-id="343c4-275">このメソッドには[StringComparison](xref:System.StringComparison) パラメーターのオプションがないため、実装する型のコンストラクターで [StringComparer](xref:System.StringComparer) を指定できるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="343c4-275">Because it does not offer the option of a [StringComparison](xref:System.StringComparison) parameter, implementing types often let the user specify a [StringComparer](xref:System.StringComparer) in their constructor.</span></span> <span data-ttu-id="343c4-276">次の例では、クラス コンストラクターに [StringComparer](xref:System.StringComparer) パラメーターを含む `FileName` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-276">The following example defines a `FileName` class whose class constructor includes a [StringComparer](xref:System.StringComparer) parameter.</span></span> <span data-ttu-id="343c4-277">この [StringComparer](xref:System.StringComparer) オブジェクトは、その後、`FileName.CompareTo` メソッドで使用されています。</span><span class="sxs-lookup"><span data-stu-id="343c4-277">This [StringComparer](xref:System.StringComparer) object is then used in the `FileName.CompareTo` method.</span></span>

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a><span data-ttu-id="343c4-278">String.Equals</span><span class="sxs-lookup"><span data-stu-id="343c4-278">String.Equals</span></span>

<span data-ttu-id="343c4-279">既定の解釈: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)。</span><span class="sxs-lookup"><span data-stu-id="343c4-279">Default interpretation: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="343c4-280">[String](xref:System.String) クラスで等価性テストを実行するには、`Equals` メソッド (静的メソッドまたはインスタンス メソッド) のオーバーロードを呼び出すか、静的等値演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-280">The [String](xref:System.String) class lets you test for equality by calling either the static or instance `Equals` method overloads, or by using the static equality operator.</span></span> <span data-ttu-id="343c4-281">これらのオーバーロードと演算子では、序数に基づく比較が既定で使用されますが、</span><span class="sxs-lookup"><span data-stu-id="343c4-281">The overloads and operator use ordinal comparison by default.</span></span> <span data-ttu-id="343c4-282">序数に基づく比較を実行する場合でも、[StringComparison](xref:System.StringComparison) 型を明示的に指定するオーバーロードを呼び出すことをお勧めします。これにより、特定の文字列解釈のコードを検索しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="343c4-282">However, we still recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type even if you want to perform an ordinal comparison; this makes it easier to search code for a certain string interpretation.</span></span> 

### <a name="stringtoupper-and-stringtolower"></a><span data-ttu-id="343c4-283">String.ToUpper と String.ToLower</span><span class="sxs-lookup"><span data-stu-id="343c4-283">String.ToUpper and String.ToLower</span></span>

<span data-ttu-id="343c4-284">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-284">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-285">これらのメソッドを使用するときには注意が必要です。というのも、文字列を大文字や小文字に強制的に変換する操作は、文字列を大文字と小文字の区別に関係なく比較するための小規模の正規化としてよく使用されるからです。</span><span class="sxs-lookup"><span data-stu-id="343c4-285">You should be careful when you use these methods, because forcing a string to a uppercase or lowercase is often used as a small normalization for comparing strings regardless of case.</span></span> <span data-ttu-id="343c4-286">その場合は、大文字と小文字を区別しない比較を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="343c4-286">If so, consider using a case-insensitive comparison.</span></span> 

<span data-ttu-id="343c4-287">[String.ToUpperInvariant](xref:System.String.ToUpperInvariant) メソッドと [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) メソッドも使用できます。</span><span class="sxs-lookup"><span data-stu-id="343c4-287">The [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) and [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) methods are also available.</span></span> <span data-ttu-id="343c4-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) は、大文字と小文字を正規化するための標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="343c4-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) is the standard way to normalize case.</span></span> <span data-ttu-id="343c4-289">[StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) を使用して行われる比較は、動作の内容を見ると、両方の文字列引数に対して [ToUpperInvariant](xref:System.String.ToUpperInvariant) を呼び出し、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) を使用して比較を行うという、2 つの呼び出しの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="343c4-289">Comparisons made using [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) are behaviorally the composition of two calls: calling [ToUpperInvariant](xref:System.String.ToUpperInvariant) on both string arguments, and doing a comparison using [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="343c4-290">特定のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを渡してそのカルチャで大文字および小文字への変換を行うためのオーバーロードもあります。</span><span class="sxs-lookup"><span data-stu-id="343c4-290">Overloads are also available for converting to uppercase and lowercase in a specific culture, by passing a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents that culture to the method.</span></span>

### <a name="chartoupper-and-chartolower"></a><span data-ttu-id="343c4-291">Char.ToUpper と Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="343c4-291">Char.ToUpper and Char.ToLower</span></span>

<span data-ttu-id="343c4-292">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-292">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-293">これらのメソッドの動作は、上で説明した [String.ToUpper](xref:System.String.ToUpper) メソッドおよび [String.ToLower](xref:System.String.ToLower) メソッドと同様です。</span><span class="sxs-lookup"><span data-stu-id="343c4-293">These methods work similarly to the [String.ToUpper](xref:System.String.ToUpper) and [String.ToLower](xref:System.String.ToLower) methods described in the previous section.</span></span>

### <a name="stringstartswith-and-stringendswith"></a><span data-ttu-id="343c4-294">String.StartsWith と String.EndsWith</span><span class="sxs-lookup"><span data-stu-id="343c4-294">String.StartsWith and String.EndsWith</span></span>

<span data-ttu-id="343c4-295">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-295">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-296">これらのメソッドは、いずれもカルチャに依存した比較を既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-296">By default, both of these methods perform a culture-sensitive comparison.</span></span>

### <a name="stringindexof-and-stringlastindexof"></a><span data-ttu-id="343c4-297">String.IndexOf と String.LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="343c4-297">String.IndexOf and String.LastIndexOf</span></span>

<span data-ttu-id="343c4-298">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-298">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-299">これらのメソッドの既定のオーバーロードは、比較の実行方法が一貫していません。</span><span class="sxs-lookup"><span data-stu-id="343c4-299">There is a lack of consistency in how the default overloads of these methods perform comparisons.</span></span> <span data-ttu-id="343c4-300">[Char](xref:System.Char) パラメーターを含むすべての [String](xref:System.String) `IndexOf` メソッドと [String](xref:System.String) `LastIndexOf` メソッドは、序数に基づく比較を実行します。一方、[String](xref:System.String) パラメーターを含む既定の [String](xref:System.String) `IndexOf` メソッドと [String`](xref:System.String) `LastIndexOf\` メソッドは、カルチャに依存した比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-300">All [String](xref:System.String) `IndexOf` and [String](xref:System.String) `LastIndexOf` methods that include a [Char](xref:System.Char) parameter perform an ordinal comparison, but the default [String](xref:System.String) `IndexOf` and [String`](xref:System.String) `LastIndexOf\` methods that include a [String](xref:System.String) parameter perform a culture-sensitive comparison.</span></span> 

<span data-ttu-id="343c4-301">` `IndexOf` or `LastIndexOf\` メソッドを呼び出して、現在のインスタンスで検索する文字列を渡す場合は、[StringComparison](xref:System.StringComparison) 型を明示的に指定するオーバーロードを呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="343c4-301">If you call ` `IndexOf` or `LastIndexOf\` method and pass it a string to locate in the current instance, we recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="343c4-302">[Char](xref:System.Char) 引数を含むオーバーロードでは、[StringComparison](xref:System.StringComparison) 型を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="343c4-302">The overloads that include a [Char](xref:System.Char) argument do not allow you to specify a [StringComparison](xref:System.StringComparison) type.</span></span>

## <a name="methods-that-perform-string-comparison-indirectly"></a><span data-ttu-id="343c4-303">間接的に文字列比較を実行するメソッド</span><span class="sxs-lookup"><span data-stu-id="343c4-303">Methods that perform string comparison indirectly</span></span>

<span data-ttu-id="343c4-304">文字列比較を中心的な操作とする非文字列メソッドの中には、[StringComparer](xref:System.StringComparer) 型を使用するものがあります。</span><span class="sxs-lookup"><span data-stu-id="343c4-304">Some non-string methods that have string comparison as a central operation use the [StringComparer](xref:System.StringComparer) type.</span></span> <span data-ttu-id="343c4-305">[StringComparer](xref:System.StringComparer) クラスには、[StringComparer](xref:System.StringComparer) のインスタンスを返す静的プロパティが 4 つ含まれています。これらのインスタンスの `Compare` メソッドは、次の種類の文字列比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="343c4-305">The [StringComparer](xref:System.StringComparer) class includes four static properties that return [StringComparer](xref:System.StringComparer) instances whose `Compare` methods perform the following types of string comparisons:</span></span>

* <span data-ttu-id="343c4-306">現在のカルチャを使用する、カルチャに依存した文字列比較。</span><span class="sxs-lookup"><span data-stu-id="343c4-306">Culture-sensitive string comparisons using the current culture.</span></span> <span data-ttu-id="343c4-307">この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-307">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) property.</span></span>

* <span data-ttu-id="343c4-308">現在のカルチャを使用する、大文字と小文字を区別しない比較。</span><span class="sxs-lookup"><span data-stu-id="343c4-308">Case-insensitive comparisons using the current culture.</span></span> <span data-ttu-id="343c4-309">この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-309">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) property.</span></span>

* <span data-ttu-id="343c4-310">序数に基づく比較。</span><span class="sxs-lookup"><span data-stu-id="343c4-310">Ordinal comparison.</span></span> <span data-ttu-id="343c4-311">この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.Ordinal](xref:System.StringComparer.Ordinal) プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-311">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.Ordinal](xref:System.StringComparer.Ordinal) property.</span></span> 

* <span data-ttu-id="343c4-312">大文字と小文字を区別しない、序数に基づく比較。</span><span class="sxs-lookup"><span data-stu-id="343c4-312">Case-insensitive ordinal comparison.</span></span> <span data-ttu-id="343c4-313">この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="343c4-313">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span>

### <a name="arraysort-and-arraybinarysearch"></a><span data-ttu-id="343c4-314">Array.Sort と Array.BinarySearch</span><span class="sxs-lookup"><span data-stu-id="343c4-314">Array.Sort and Array.BinarySearch</span></span>

<span data-ttu-id="343c4-315">既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="343c4-315">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="343c4-316">データをコレクションに格納したり、永続化されたデータをファイルやデータベースからコレクションに読み取ったりするときに現在のカルチャを切り替えると、コレクション内のインバリアントが無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-316">When you store any data in a collection, or read persisted data from a file or database into a collection, switching the current culture can invalidate the invariants in the collection.</span></span> <span data-ttu-id="343c4-317">[Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) メソッドでは、配列内で検索する要素が既に並べ替えられていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="343c4-317">The [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) method assumes that the elements in the array to be searched are already sorted.</span></span> <span data-ttu-id="343c4-318">[Array.Sort](xref:System.Array.Sort(System.Array)) メソッドは、配列内の文字列要素を並べ替えるために、[String] `Compare` メソッドを呼び出して個々の要素を順序付けます。</span><span class="sxs-lookup"><span data-stu-id="343c4-318">To sort any string element in the array, the [Array.Sort](xref:System.Array.Sort(System.Array)) method calls the [String] `Compare` method to order individual elements.</span></span> <span data-ttu-id="343c4-319">配列の並べ替えが行われてから内容の検索が行われるまでの間にカルチャが変更される場合、カルチャに依存した比較子を使用するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="343c4-319">Using a culture-sensitive comparer can be dangerous if the culture changes between the time that the array is sorted and its contents are searched.</span></span> <span data-ttu-id="343c4-320">たとえば、次のコードでは、`Thread.CurrentThread.CurrentCulture` プロパティによって暗黙的に提供される比較子で格納と取得の操作が行われています。</span><span class="sxs-lookup"><span data-stu-id="343c4-320">For example, in the following code, storage and retrieval operate on the comparer that is provided implicitly by the `Thread.CurrentThread.CurrentCulture` property.</span></span> <span data-ttu-id="343c4-321">`StoreNames` の呼び出しと `DoesNameExist` の呼び出しの間にカルチャが変更されると (この 2 つのメソッドの呼び出しの間に配列の内容が永続化された場合には特に)、バイナリ サーチが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-321">If the culture can change between the calls to `StoreNames` and `DoesNameExist`, and especially if the array contents are persisted somewhere between the two method calls, the binary search may fail.</span></span> 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

<span data-ttu-id="343c4-322">次の例は、推奨されるバリエーションを示しています。ここでは、配列の並べ替えと検索の両方に、同じ序数に基づく (カルチャに依存しない) 比較メソッドが使用されています。</span><span class="sxs-lookup"><span data-stu-id="343c4-322">A recommended variation appears in the following example, which uses the same ordinal (culture-insensitive) comparison method both to sort and to search the array.</span></span> <span data-ttu-id="343c4-323">コードの変更は、2 つの例の `Line A` および `Line B` というラベルが付いた行に反映されています。</span><span class="sxs-lookup"><span data-stu-id="343c4-323">The change code is reflected in the lines labeled `Line A` and `Line B` in the two examples.</span></span>

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

<span data-ttu-id="343c4-324">このデータを永続化して別のカルチャのシステムに移動したり、データをユーザーに表示するために並べ替えたりする場合は、`StringComparison.InvariantCulture` を使用することを検討してください。そうすると、ユーザー出力のために言語的な操作を行っても、カルチャの変更による影響を受けることはありません。</span><span class="sxs-lookup"><span data-stu-id="343c4-324">If this data is persisted and moved across cultures, and sorting is used to present this data to the user, you might consider using `StringComparison.InvariantCulture`, which operates linguistically for better user output but is unaffected by changes in culture.</span></span> <span data-ttu-id="343c4-325">次の例では、前の 2 つの例を変更して、配列の並べ替えと検索にインバリアント カルチャを使用しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-325">The following example modifies the two previous examples to use the invariant culture for sorting and searching the array.</span></span>

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a><span data-ttu-id="343c4-326">コレクションの例: Hashtable のコンストラクター</span><span class="sxs-lookup"><span data-stu-id="343c4-326">Collections Example: Hashtable Constructor</span></span>

<span data-ttu-id="343c4-327">文字列のハッシュも、文字列の比較方法の影響を受ける操作の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="343c4-327">Hashing strings provides a second example of an operation that is affected by the way in which strings are compared.</span></span> 

<span data-ttu-id="343c4-328">次の例では、[StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) プロパティによって返される [StringComparer](xref:System.StringComparer) オブジェクトを渡すことによって [Hashtable](xref:System.Collections.Hashtable) オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="343c4-328">The following example instantiates a [Hashtable](xref:System.Collections.Hashtable) object by passing it the [StringComparer](xref:System.StringComparer) object that is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span> <span data-ttu-id="343c4-329">[StringComparer](xref:System.StringComparer) から派生するクラス [StringComparer](xref:System.StringComparer)は [IEqualityComparer](xref:System.Collections.IEqualityComparer) インターフェイスを実装するため、その [GetHashCode](xref:System.Collections.IEqualityComparer) メソッドを使用して、ハッシュ テーブルの文字列のハッシュ コードを計算しています。</span><span class="sxs-lookup"><span data-stu-id="343c4-329">Because a class [StringComparer](xref:System.StringComparer) that is derived from [StringComparer](xref:System.StringComparer) implements the [IEqualityComparer](xref:System.Collections.IEqualityComparer) interface, its [GetHashCode](xref:System.Collections.IEqualityComparer) method is used to compute the hash code of strings in the hash table.</span></span>

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a><span data-ttu-id="343c4-330">書式設定されたデータを表示および保持する</span><span class="sxs-lookup"><span data-stu-id="343c4-330">Displaying and persisting formatted data</span></span>

<span data-ttu-id="343c4-331">数値、日時など、文字列以外のデータをユーザーに表示するには、ユーザーのカルチャ設定を使用して書式設定します。</span><span class="sxs-lookup"><span data-stu-id="343c4-331">When you display non-string data such as numbers and dates and times to users, format them by using the user's cultural settings.</span></span> <span data-ttu-id="343c4-332">既定では、数値型と日時型の [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドと `ToString` メソッドは、書式設定の操作に現在のスレッド カルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="343c4-332">By default, the [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) method and the `ToString` methods of the numeric types and the date and time types use the current thread culture for formatting operations.</span></span> <span data-ttu-id="343c4-333">書式設定メソッドで現在のカルチャを使用することを明示的に指定するには、provider パラメーターを含む書式設定メソッド ([String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))、[DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) など) のオーバーロードを呼び出して、そのパラメーターを [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) プロパティに渡します。</span><span class="sxs-lookup"><span data-stu-id="343c4-333">To explicitly specify that the formatting method should use the current culture, you can call an overload of a formatting method that has a provider parameter, such as [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) or [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)), and pass it the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property.</span></span> 

<span data-ttu-id="343c4-334">文字列以外のデータは、バイナリ データまたは書式付きデータとして保持できます。</span><span class="sxs-lookup"><span data-stu-id="343c4-334">You can persist non-string data either as binary data or as formatted data.</span></span> <span data-ttu-id="343c4-335">書式付きデータとして保存するには、*provider* パラメーターを含む書式指定メソッドのオーバーロードを呼び出し、そのパラメーターを [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-335">If you choose to save it as formatted data, you should call a formatting method overload that includes a *provider* parameter and pass it the [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="343c4-336">インバリアント カルチャは、カルチャとコンピューターに依存しない書式付きデータに一貫した書式を提供します。</span><span class="sxs-lookup"><span data-stu-id="343c4-336">The invariant culture provides a consistent format for formatted data that is independent of culture and machine.</span></span> <span data-ttu-id="343c4-337">これに対し、インバリアント カルチャ以外のカルチャを使用して書式設定するデータの保持には、さまざまな制限があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-337">In contrast, persisting data that is formatted by using cultures other than the invariant culture has a number of limitations:</span></span> 

* <span data-ttu-id="343c4-338">カルチャが異なるシステムでデータを取得したり、現在のシステムのユーザーが現在のカルチャを変更してデータを取得しようとしたりすると、そのデータは使用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-338">The data is likely to be unusable if it is retrieved on a system that has a different culture, or if the user of the current system changes the current culture and tries to retrieve the data.</span></span> 

* <span data-ttu-id="343c4-339">特定のコンピューターのカルチャのプロパティは、その標準の値とは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-339">The properties of a culture on a specific computer can differ from standard values.</span></span> <span data-ttu-id="343c4-340">常に、ユーザーはカルチャに依存した表示設定をカスタマイズする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-340">At any time, a user can customize culture-sensitive display settings.</span></span> <span data-ttu-id="343c4-341">このため、ユーザーがカルチャの設定をカスタマイズすると、システムに保存されている書式付きデータが読み取ることができなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-341">Because of this, formatted data that is saved on a system may not be readable after the user customizes cultural settings.</span></span> <span data-ttu-id="343c4-342">コンピューター間の書式付きデータの移植性がさらに制限される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-342">The portability of formatted data across computers is likely to be even more limited.</span></span> 

* <span data-ttu-id="343c4-343">数値や日時の書式設定を制御する国際的、地域的、または国内の標準は時間と共に変化するため、これらの変化はオペレーティング システムの更新プログラムに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="343c4-343">International, regional, or national standards that govern the formatting of numbers or dates and times change over time, and these changes are incorporated into operating system updates.</span></span> <span data-ttu-id="343c4-344">書式設定の規則が変わると、以前の規則に従って書式設定されたデータが読み取ることができなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="343c4-344">When formatting conventions change, data that was formatted by using the previous conventions may become unreadable.</span></span> 

<span data-ttu-id="343c4-345">次に、カルチャに依存する書式設定を使用してデータを保持すると移植性が制限される例を示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-345">The following example illustrates the limited portability that results from using culture-sensitive formatting to persist data.</span></span> <span data-ttu-id="343c4-346">この例では、日時の値の配列をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="343c4-346">The example saves an array of date and time values to a file.</span></span> <span data-ttu-id="343c4-347">これらは、英語 (米国) のカルチャの規則を使用して書式設定されています。</span><span class="sxs-lookup"><span data-stu-id="343c4-347">These are formatted by using the conventions of the English (United States) culture.</span></span> <span data-ttu-id="343c4-348">現在のスレッド カルチャがフランス語 (スイス) に変更されると、アプリケーションは現在のカルチャの書式設定規則を使用して保存された値を読み取ることを試みます。</span><span class="sxs-lookup"><span data-stu-id="343c4-348">After the application changes the current thread culture to French (Switzerland), it tries to read the saved values by using the formatting conventions of the current culture.</span></span> <span data-ttu-id="343c4-349">2 つのデータ項目の読み取りを試みると、[FormatException](xref:System.FormatException) 例外がスローされます。日付の配列には、[MinValue](xref:System.DateTime.MinValue) に等しい 2 つの間違った要素が含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="343c4-349">The attempt to read two of the data items throws a [FormatException](xref:System.FormatException) exception, and the array of dates now contains two incorrect elements that are equal to [MinValue](xref:System.DateTime.MinValue).</span></span> 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

<span data-ttu-id="343c4-350">ただし、[DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 呼び出しと [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)) 呼び出しで [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) プロパティを [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) に置き換えると、保持されている日時データは正常に復元されます。次にその出力を示します。</span><span class="sxs-lookup"><span data-stu-id="343c4-350">However, if you replace the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property with [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) in the calls to [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), the persisted date and time data is successfully restored, as the following output shows.</span></span>

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a><span data-ttu-id="343c4-351">関連項目</span><span class="sxs-lookup"><span data-stu-id="343c4-351">See also</span></span>

[<span data-ttu-id="343c4-352">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="343c4-352">Manipulating strings</span></span>](manipulating-strings.md)

