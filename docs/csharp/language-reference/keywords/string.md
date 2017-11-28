---
title: "string (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87df2b158b173072aad5257594e1b1482ae61067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="string-c-reference"></a><span data-ttu-id="6b75f-102">string (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6b75f-102">string (C# Reference)</span></span>
<span data-ttu-id="6b75f-103">`string` 型は、0 個以上の Unicode 文字のシーケンスを表します。</span><span class="sxs-lookup"><span data-stu-id="6b75f-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="6b75f-104">`string` は、.NET Framework の <xref:System.String> のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="6b75f-104">`string` is an alias for <xref:System.String> in the .NET Framework.</span></span>  
  
 <span data-ttu-id="6b75f-105">`string` は参照型ですが、等値演算子 (`==` および `!=`) は、`string` オブジェクトの参照ではなく、値を比較するように定義されています。</span><span class="sxs-lookup"><span data-stu-id="6b75f-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="6b75f-106">これにより、文字列が等しいかを直感的にテストできます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="6b75f-107">例:</span><span class="sxs-lookup"><span data-stu-id="6b75f-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="6b75f-108">文字列の内容が等しいので、"True"、"False" の順に表示されますが、`a` および `b` は同じ文字列インスタンスを参照しません。</span><span class="sxs-lookup"><span data-stu-id="6b75f-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="6b75f-109">+ 演算子は、文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="6b75f-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="6b75f-110">これは、"good morning" を含む文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b75f-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="6b75f-111">文字列は "*変更不可*" です。文字列オブジェクトの作成後、そのコンテンツを変更することはできません。構文では変更可能に見えても、変更不可です。</span><span class="sxs-lookup"><span data-stu-id="6b75f-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="6b75f-112">たとえば、このコードを作成すると、コンパイラによって新しい文字列オブジェクトを格納する新しいシーケンス オブジェクトが生成され、その新しいオブジェクトが b に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="6b75f-113">そして、文字列 "h" がガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="6b75f-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="6b75f-114">[] 演算子は、`string` の各文字への読み取り専用アクセスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="6b75f-115">リテラル文字列は `string` 型であり、二重引用符で囲む形式と、@-quoted 形式の 2 とおりがあります。</span><span class="sxs-lookup"><span data-stu-id="6b75f-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="6b75f-116">二重引用符で囲む場合は、リテラル文字列の前後に二重引用符 (") を付けます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="6b75f-117">リテラル文字列には、任意の文字リテラルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-117">String literals can contain any character literal.</span></span> <span data-ttu-id="6b75f-118">これにはエスケープ シーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-118">Escape sequences are included.</span></span> <span data-ttu-id="6b75f-119">次の例では、円記号にエスケープ シーケンス `\\`、文字 f に `\u0066`、改行に `\n` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="6b75f-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="6b75f-120">エスケープ コード `\udddd` (`dddd` は 4 桁の数字) は、Unicode 文字 U +`dddd` を表します。</span><span class="sxs-lookup"><span data-stu-id="6b75f-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="6b75f-121">8 桁の Unicode エスケープ コード `\Udddddddd` も認識できます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="6b75f-122">verbatim 文字列リテラルの場合は、先頭に @ を付け、さらに前後に二重引用符を付けます。</span><span class="sxs-lookup"><span data-stu-id="6b75f-122">Verbatim string literals start with @ and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="6b75f-123">例:</span><span class="sxs-lookup"><span data-stu-id="6b75f-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="6b75f-124">verbatim 文字列の場合の利点は、エスケープ シーケンスが "*処理されない*" ため、たとえば、完全修飾ファイル名が書きやすくなることです。</span><span class="sxs-lookup"><span data-stu-id="6b75f-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="6b75f-125">@-quoted 文字列に二重引用符を含めるには、二重引用符を二重にします。</span><span class="sxs-lookup"><span data-stu-id="6b75f-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="6b75f-126">また、C# キーワードである参照 ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) 識別子を使用する場合も、@ 記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b75f-126">Another use of the @ symbol is to use referenced ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifiers that are C# keywords.</span></span>  
  
 <span data-ttu-id="6b75f-127">C# での文字列の詳細については、「[文字列](../../../csharp/programming-guide/strings/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b75f-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b75f-128">例</span><span class="sxs-lookup"><span data-stu-id="6b75f-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6b75f-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6b75f-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b75f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b75f-130">See Also</span></span>  
 [<span data-ttu-id="6b75f-131">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6b75f-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6b75f-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6b75f-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6b75f-133">文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6b75f-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
 [<span data-ttu-id="6b75f-134">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="6b75f-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6b75f-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6b75f-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6b75f-136">参照型</span><span class="sxs-lookup"><span data-stu-id="6b75f-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="6b75f-137">値型</span><span class="sxs-lookup"><span data-stu-id="6b75f-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="6b75f-138">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="6b75f-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="6b75f-139">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="6b75f-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="6b75f-140">数値結果テーブルの書式設定</span><span class="sxs-lookup"><span data-stu-id="6b75f-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
