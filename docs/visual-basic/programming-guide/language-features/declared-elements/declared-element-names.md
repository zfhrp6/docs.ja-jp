---
title: "宣言された要素の名前 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 56ac0684e5176f33aa6f9600f20d9fe3fcf09416
ms.lasthandoff: 03/13/2017

---
# <a name="declared-element-names-visual-basic"></a>宣言された要素の名前 (Visual Basic)
どの宣言された要素にも、名前とも呼ばれます、*識別子*、これは、コードを使用してそれを参照してください。  
  
## <a name="rules"></a>ルール  
 内の要素名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]次の規則に従う必要があります。  
  
-   文字は英字またはアンダー スコアで始まる必要があります (`_`)。  
  
-   アルファベット文字、10 進数字およびアンダー スコアのみでなければなりません。  
  
-   アンダー スコアで始まる場合、少なくとも&1; つのアルファベット文字または&10; 進数字でなければなりません。  
  
-   1023 を超える文字はできません。  
  
 1023 文字の長さの制限にも適用されます、完全修飾名の文字列全体など`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`します。  
  
 次の例では、有効な要素名を示します。  
  
 `aB123__45`  
  
 `_567`  
  
 次の例では、無効な要素名を示します。 最初には、アンダー スコアのみが含まれています。、2 つ目が&10; 進数字で始まるおよび&3; つ目には、無効な文字 ($) が含まれています。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  アンダー スコアで始まる要素名 (`_`) に含まれていませんが、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、CLS 準拠のコードはそのような名前を定義するコンポーネントを使用できないようにします。 ただし、要素名の他の任意の位置にアンダー スコアでは、CLS に準拠します。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、自分の名前は、できるだけ短く要素の特性を明確します。 これにより、コードの読みやすさを向上し、行の長さとソース ファイルのサイズを小さきます。  
  
 これに対して、自分の名前は、いない適切に記述できる要素が表す意味を調べると、コードがこれを使用する方法長さである必要があります。 これは、コードの読みやすさにとって重要です。 使い方も理解しようとする他の人がいる場合、または自分で検索する場合に作成した後、長い時間は、適切な要素名は、かなりの時間を保存できます。  
  
## <a name="escaped-names"></a>エスケープされた名前  
 一般に、要素名は、必要がありますと一致しませんによって予約されているキーワードのいずれかの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]など`Case`または`Friend`です。 ただし、定義することができます、*エスケープ名前*、角かっこで囲まれている (`[ ]`)。 エスケープされた名前がいずれかに一致[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]キーワード、角かっこは、任意のあいまいさを排除するためです。 後続のコードで名前を参照する場合は、角かっこを使用します。  
  
 一般に、エスケープされた名前を使用する必要がありますされる場合にのみ。  
  
-   以前のバージョンから移行済みのコードは[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は名として使用されているキーワードが予約されていないか、  
  
-   特定のキーワードは予約されていない別の言語で記述されたコードを使用しています。  
  
 それ以外の場合、キーワードを使用してその名前が競合している場合、要素名の変更を検討してください。 統合開発環境 (IDE) では、これを行う簡単な方法を提供します。 詳細については、次を参照してください。[リファクタリング](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb)します。  
  
## <a name="case-sensitivity-in-names"></a>名前に大文字小文字の区別  
 内の要素名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]小文字は区別されません。 これは、コンパイラは、大文字と小文字だけが異なる&2; つの名前を比較し、ときと解釈するに同じ名前を意味します。 たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 ただし、共通言語ランタイム (CLR) は、大文字小文字を区別バインディングを使用します。 このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。 たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。 かどうかは後で、クラスを再コンパイルし、要素の名前を変更する`abc`クラスを使用して、他のアセンブリがその要素にアクセスできなくします。 したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。  
  
## <a name="names-and-locales"></a>名前およびロケール  
 名前の比較ではロケールに依存しません。 1 つのロケールで&2; つの名前が同じ場合は、すべてのロケールに一致するように、保証されます。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
