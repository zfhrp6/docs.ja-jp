---
title: "string (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
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
ms.openlocfilehash: 56847aad4cb8b0427594a299df2306d21675506b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="string-c-reference"></a><span data-ttu-id="df102-102">string (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="df102-102">string (C# Reference)</span></span>
<span data-ttu-id="df102-103">`string` 型は、0 個以上の Unicode 文字のシーケンスを表します。</span><span class="sxs-lookup"><span data-stu-id="df102-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="df102-104">`string` は、.NET Framework の <xref:System.String> のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="df102-104">`string` is an alias for <xref:System.String> in the .NET Framework.</span></span>  
  
 <span data-ttu-id="df102-105">`string` は参照型ですが、等値演算子 (`==` および `!=`) は、`string` オブジェクトの参照ではなく、値を比較するように定義されています。</span><span class="sxs-lookup"><span data-stu-id="df102-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="df102-106">これにより、文字列が等しいかを直感的にテストできます。</span><span class="sxs-lookup"><span data-stu-id="df102-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="df102-107">例:</span><span class="sxs-lookup"><span data-stu-id="df102-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="df102-108">文字列の内容が等しいので、"True"、"False" の順に表示されますが、`a` および `b` は同じ文字列インスタンスを参照しません。</span><span class="sxs-lookup"><span data-stu-id="df102-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="df102-109">+ 演算子は、文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="df102-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="df102-110">これは、"good morning" を含む文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="df102-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="df102-111">文字列は "*変更不可*" です。文字列オブジェクトの作成後、そのコンテンツを変更することはできません。構文では変更可能に見えても、変更不可です。</span><span class="sxs-lookup"><span data-stu-id="df102-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="df102-112">たとえば、このコードを作成すると、コンパイラによって新しい文字列オブジェクトを格納する新しいシーケンス オブジェクトが生成され、その新しいオブジェクトが b に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="df102-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="df102-113">そして、文字列 "h" がガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="df102-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="df102-114">[] 演算子は、`string` の各文字への読み取り専用アクセスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="df102-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="df102-115">リテラル文字列は `string` 型であり、二重引用符で囲む形式と、@-quoted 形式の 2 とおりがあります。</span><span class="sxs-lookup"><span data-stu-id="df102-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="df102-116">二重引用符で囲む場合は、リテラル文字列の前後に二重引用符 (") を付けます。</span><span class="sxs-lookup"><span data-stu-id="df102-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="df102-117">リテラル文字列には、任意の文字リテラルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="df102-117">String literals can contain any character literal.</span></span> <span data-ttu-id="df102-118">これにはエスケープ シーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="df102-118">Escape sequences are included.</span></span> <span data-ttu-id="df102-119">次の例では、円記号にエスケープ シーケンス `\\`、文字 f に `\u0066`、改行に `\n` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="df102-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="df102-120">エスケープ コード `\udddd` (`dddd` は 4 桁の数字) は、Unicode 文字 U +`dddd` を表します。</span><span class="sxs-lookup"><span data-stu-id="df102-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="df102-121">8 桁の Unicode エスケープ コード `\Udddddddd` も認識できます。</span><span class="sxs-lookup"><span data-stu-id="df102-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="df102-122">verbatim 文字列リテラルの場合は、先頭に @ を付け、さらに前後に二重引用符を付けます。</span><span class="sxs-lookup"><span data-stu-id="df102-122">Verbatim string literals start with @ and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="df102-123">例:</span><span class="sxs-lookup"><span data-stu-id="df102-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="df102-124">verbatim 文字列の場合の利点は、エスケープ シーケンスが "*処理されない*" ため、たとえば、完全修飾ファイル名が書きやすくなることです。</span><span class="sxs-lookup"><span data-stu-id="df102-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="df102-125">@-quoted 文字列に二重引用符を含めるには、二重引用符を二重にします。</span><span class="sxs-lookup"><span data-stu-id="df102-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="df102-126">また、C# キーワードである参照 ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) 識別子を使用する場合も、@ 記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="df102-126">Another use of the @ symbol is to use referenced ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifiers that are C# keywords.</span></span>  
  
 <span data-ttu-id="df102-127">C# での文字列の詳細については、「[文字列](../../../csharp/programming-guide/strings/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df102-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df102-128">例</span><span class="sxs-lookup"><span data-stu-id="df102-128">Example</span></span>  
 <span data-ttu-id="df102-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="df102-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="df102-130">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="df102-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df102-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="df102-131">See Also</span></span>  
 <span data-ttu-id="df102-132">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="df102-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="df102-133">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="df102-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="df102-134">[文字列を使用するためのベスト プラクティス](../../../standard/base-types/best-practices-strings.md) </span><span class="sxs-lookup"><span data-stu-id="df102-134">[Best Practices for Using Strings](../../../standard/base-types/best-practices-strings.md) </span></span>  
 <span data-ttu-id="df102-135">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="df102-135">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="df102-136">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="df102-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="df102-137">[参照型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="df102-137">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="df102-138">[値型](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="df102-138">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="df102-139">[基本的な文字列操作](../../../standard/base-types/basic-string-operations.md) </span><span class="sxs-lookup"><span data-stu-id="df102-139">[Basic String Operations](../../../standard/base-types/basic-string-operations.md) </span></span>  
 <span data-ttu-id="df102-140">[新しい文字列の作成](../../../standard/base-types/creating-new.md) </span><span class="sxs-lookup"><span data-stu-id="df102-140">[Creating New Strings](../../../standard/base-types/creating-new.md) </span></span>  
 [<span data-ttu-id="df102-141">数値結果テーブルの書式設定</span><span class="sxs-lookup"><span data-stu-id="df102-141">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)

