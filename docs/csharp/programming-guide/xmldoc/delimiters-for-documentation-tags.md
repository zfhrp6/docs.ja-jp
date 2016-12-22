---
title: "ドキュメント タグの区切り記号 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# ドキュメント タグの /** */ 区切り記号"
  - "C# ドキュメントの /// 区切り記号"
  - "XML [C#], 区切り記号"
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ドキュメント タグの区切り記号 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

XML ドキュメント コメントでは区切り記号を使用して、ドキュメント コメントの開始位置と終了位置をコンパイラに示す必要があります。  XML ドキュメント タグでは、次の種類の区切り記号を使用できます。  
  
 `///`  
 単一行の区切り記号  ドキュメント例で使用されています。この区切り記号は、Visual C\# プロジェクト テンプレートで使用されます。  区切り記号の後に空白文字がある場合、その文字は XML 出力に含まれません。  
  
> [!NOTE]
>  Visual Studio IDE には、スマート コメント編集と呼ばれる機能があります。コード エディターで `///` 区切り記号を入力すると、\<summary\> タグと \<\/summary\> タグが自動的に挿入され、これらのタグの内側にカーソルが移動します。  この機能には、プロジェクト プロパティ ページの [\[オプション\]、\[テキスト エディター\]、\[C\#\]、\[書式設定\]](/visual-studio/ide/reference/options-text-editor-csharp-formatting)からアクセスします。  
  
 `/** */`  
 複数行の区切り記号  
  
 `/** */` を使用する場合は、次の書式指定規則に従う必要があります。  
  
-   `/**`  区切り記号がある行で、行の残りの部分が空白の場合は、その行がコメントとして扱われません。  `/**`  区切り記号の後の最初の文字が空白の場合、その空白文字は無視され、行の残りの部分が処理されます。  それ以外の場合は、`/**` 区切り記号の後にある行のテキスト全体が、コメントの一部として扱われます。  
  
-   `*/`  区切り記号がある行で、`*/` 区切り記号までの部分がすべて空白の場合は、その行が無視されます。  それ以外の場合は、以下の箇条書きで説明するパターン一致規則に従って、その行の `*/` 区切り記号までのテキストがコメントの一部として扱われます。  
  
-   `/**` 区切り記号で始まる行の後に来る行の場合、コンパイラは各行の先頭で共通のパターンを検索します。  このパターンとして指定できるのは、空白 \(省略可能\) \+ アスタリスク \(`*`\) \+ 空白 \(省略可能\) です。  `/**` 区切り記号または `*/` 区切り記号で始まらない各行の先頭で、コンパイラが共通のパターンを検索する場合、各行のそのパターンは無視されます。  
  
 これらの規則について、次の例で説明します。  
  
-   次の例では、`<summary>` で始まる行だけがコメントの一部として扱われます。  次の 3 とおりの形式のタグは、いずれも同じコメントを生成します。  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
  
    ```  
  
-   コンパイラは、2 行目と 3 行目の先頭で共通のパターン " \* " を識別します。  このパターンは出力に含まれません。  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   次のコメントでは、3 行目の 2 番目の文字がアスタリスクではないため、コンパイラは共通のパターンを検索しません。  このため、2 行目のすべてのテキストと 3 行目が、コメントの一部として扱われます。  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   次のコメントでは、2 つの原因によりパターンが見つかりません。  第 1 に、アスタリスクの前の空白の数が一致していません。  第 2 に、5 行目がタブで始まっています。空白とタブは一致しません。  このため、2 行目から 5 行目のすべてのテキストが、コメントの一部として扱われます。  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)