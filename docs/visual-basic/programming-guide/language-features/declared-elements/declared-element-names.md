---
title: "Declared Element Names (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared elements, case sensitivity"
  - "names, Visual Basic rules"
  - "naming conventions"
  - "element names"
  - "declared elements, identifiers"
  - "declarations, elements"
  - "declared elements, valid names"
  - "[] escape characters [Visual Basic]"
  - "names, elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "identifiers, declared elements"
  - "case sensitivity, declared element names"
  - "escape characters"
  - "names, declared elements"
  - "declared elements, about declared elements"
  - "escaped names"
  - "declared elements, names"
  - "names, naming conventions"
  - "identifiers, elements"
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Declared Element Names (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

すべての宣言された要素には名前があります。この名前は*識別子*とも呼ばれ、宣言された要素をコードで参照するときに使用します。  
  
## 規則  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] での要素名は、次の規則に従う必要があります。  
  
-   アルファベットまたはアンダースコア \(`_`\) で始まる。  
  
-   アルファベット、10 進数、アンダースコア以外の文字を含まない。  
  
-   アンダースコアで始まる場合は、アルファベットまたは 10 進数を少なくとも 1 文字含む必要がある。  
  
-   長さが 1023 文字を超えない。  
  
 最大 1023 文字の制限は、`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` などの完全修飾名の文字列全体にも適用されます。  
  
 有効な要素名の例を次に示します。  
  
 `aB123__45`  
  
 `_567`  
  
 無効な要素名の例を次に示します。  1 番目はアンダースコアだけを含み、2 番目は 10 進数で始まり、3 番目には無効な文字 \($\) が含まれています。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  アンダースコア \(`_`\) で始まる要素名は [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) になりません。したがって、CLS 準拠のコードはそのような名前を定義したコンポーネントを使用できません。  ただし、先頭以外であれば、要素名のどの位置にアンダースコアを使用しても CLS 準拠になります。  
  
### 名前の長さのガイドライン  
 実際の問題として、名前は、要素の特性を明確に区別しながら可能な限り短いものである必要があります。  これによってコードが読みやすくなり、行の長さとソース ファイルのサイズを小さくできます。  
  
 一方で、開発者の名前は、要素が何を表すのか、さらにコードで要素を使用する方法を適切に記述できる長さである必要があります。  これは、コードの読みやすさの点で重要です。  だれかが理解しようとした場合、または開発者自身がこれを作成した後しばらくたってからこれを見たときに、適切な要素名が付いていると時間を節約できます。  
  
## エスケープされた名前  
 通常は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって予約されているキーワード \(`Case` や `Friend` など\) と一致する名前を要素名として使用することはできません。  ただし、名前を角かっこ \(`[ ]`\) で囲んで、*エスケープされた名前*として定義できます。  角かっこによってあいまいさがなくなるため、エスケープされた名前では、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のキーワードと一致する名前を使用できます。  定義した名前を後でコード内で使用するときも、同じように角かっこで囲みます。  
  
 一般には、エスケープされた名前を使用するのは次の場合だけです。  
  
-   コードが、名前として使用されている用語がキーワードとして予約されていない、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の前のバージョンから移行されたものである。  
  
-   指定されたキーワードが予約されていない別の言語で作成されたコードを使用している。  
  
 それ以外の場合で名前がキーワードと競合した場合は、要素名の変更を検討する必要があります。  統合開発環境 \(IDE: Integrated Development Environment\) には、これを行うための簡単な方法が用意されています。  詳細については、「[リファクタリングと \[名前の変更\] ダイアログ ボックス](../../../../visual-basic/developing-apps/using-ide/refactoring-and-rename-dialog-box.md)」を参照してください。  
  
## 名前の大文字と小文字の区別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の要素名は、大文字と小文字を区別します。  したがって、大文字と小文字だけで区別される 2 つの名前は、コンパイラによって同じ名前であると解釈されます。  たとえば、`ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 しかし、共通言語ランタイム \(CLR: Common Language Runtime\) のバインディングでは大文字と小文字が区別されます。  このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにする場合は、大文字と小文字が区別されるようになります。  たとえば、`ABC` という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC` として参照する必要があります。  後でクラスを再コンパイルして要素の名前を `abc` に変更すると、このクラスを使用していた他のアセンブリがこの要素にアクセスできなくなります。  したがって、アセンブリを更新してリリースするときには、パブリックな要素の名前の大文字と小文字を変更しないようにする必要があります。  
  
## 名前およびロケール  
 名前の比較はロケールには依存しません。  1 つのロケール内で 2 つの名前が一致した場合、これはすべてのロケールで一致することになります。  
  
## 参照  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)