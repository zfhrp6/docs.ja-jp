---
title: "ドキュメント タグの区切り記号 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a6ab03d220d1ef71605b83c529595dd986ea922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="aaa7f-102">ドキュメント タグの区切り記号 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="aaa7f-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="aaa7f-103">XML ドキュメント コメントでは区切り記号を使用し、ドキュメント コメントの開始位置と終了位置をコンパイラに示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="aaa7f-104">XML ドキュメント タグでは、次の種類の区切り記号を使用できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="aaa7f-105">単一行の区切り記号。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-105">Single-line delimiter.</span></span> <span data-ttu-id="aaa7f-106">ドキュメント例で使用されています。この区切り記号は、Visual C# プロジェクト テンプレートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="aaa7f-107">区切り記号の直後に空白文字が続く場合、その文字は XML 出力に含まれません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaa7f-108">Visual Studio IDE には、スマート コメント編集と呼ばれる機能があります。コード エディターで `///` 区切り記号を入力すると、\<summary> タグと \</summary> タグが自動的に挿入され、これらのタグの内側にカーソルが移動します。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="aaa7f-109">この機能には、プロジェクト プロパティ ページの [[オプション]、[テキスト エディター]、[C#]、[書式設定]](/visualstudio/ide/reference/options-text-editor-csharp-formatting) からアクセスします。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-109">Access this feature from the [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting) in your project property pages.</span></span>  
  
 `/** */`  
 <span data-ttu-id="aaa7f-110">複数行の区切り記号。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="aaa7f-111">`/** */` 区切り記号を使用する場合は、次の書式設定規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="aaa7f-112">`/**` 区切り記号がある行で、行の残りの部分が空白の場合、その行はコメントとして処理されません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="aaa7f-113">`/**` 区切り記号の後の最初の文字が空白の場合、その空白文字は無視され、行の残りの部分が処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="aaa7f-114">それ以外の場合、`/**` 区切り記号の後にある行のテキスト全体が、コメントの一部として処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="aaa7f-115">`*/` 区切り記号がある行で、`*/` 区切り記号までの部分がすべて空白の場合、その行は無視されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="aaa7f-116">それ以外の場合、以下の箇条書きで説明するパターン一致規則に従って、その行の `*/` 区切り記号までのテキストがコメントの一部として処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="aaa7f-117">`/**` 区切り記号で始まる行の後に来る行については、コンパイラは各行の先頭で共通のパターンを検索します。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="aaa7f-118">このパターンは、空白 (省略可能) + アスタリスク (`*`) + 空白 (省略可能) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="aaa7f-119">`/**` 区切り記号または `*/` 区切り記号で始まらない各行の先頭でコンパイラが共通のパターンを見つけた場合、各行のそのパターンは無視されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="aaa7f-120">これらの規則について、次の例で説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="aaa7f-121">次のコメントでは、`<summary>` で始まる行だけがコメントの一部として処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="aaa7f-122">次の 3 つのタグ形式は、いずれも同じコメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="aaa7f-123">コンパイラは、2 行目と 3 行目の先頭で共通のパターン " * " を識別します。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-123">The compiler identifies a common pattern of " * " at the beginning of the second and third lines.</span></span> <span data-ttu-id="aaa7f-124">このパターンは出力に含まれません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="aaa7f-125">次のコメントでは、3 行目の 2 番目の文字がアスタリスクではないため、コンパイラは共通のパターンを検索しません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="aaa7f-126">このため、2 行目と 3 行目のすべてのテキストがコメントの一部として処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="aaa7f-127">次のコメントでは、2 つの原因によりコンパイラはパターンを検出しません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="aaa7f-128">まず、アスタリスクの前の空白の数が一致していません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="aaa7f-129">次に、5 行目がタブで始まっています。空白とタブは一致しません。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="aaa7f-130">このため、2 行目から 5 行目のすべてのテキストがコメントの一部として処理されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7f-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="aaa7f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="aaa7f-131">See Also</span></span>  
 [<span data-ttu-id="aaa7f-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="aaa7f-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aaa7f-133">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="aaa7f-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="aaa7f-134">/doc (c# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="aaa7f-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="aaa7f-135">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="aaa7f-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
