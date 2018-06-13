---
title: 宣言された要素の名前 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 2f48f885b66f99ecc8c6c7e13fea7e75f0e3d24a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651480"
---
# <a name="declared-element-names-visual-basic"></a>宣言された要素の名前 (Visual Basic)
すべての宣言された要素とも呼ばれる、名前が付いて、*識別子*、これは、コードを使用して、それを参照してください。  
  
## <a name="rules"></a>ルール  
 Visual Basic では、要素名は、次の規則に従う必要があります。  
  
-   文字は英字またはアンダー スコアで始める必要があります (`_`)。  
  
-   英字、十進数、およびアンダー スコアのみでなければなりません。  
  
-   アンダー スコアで始まる場合、少なくとも 1 つの文字が英字または 10 進数字でなければなりません。  
  
-   長さが 1023 文字はできません。  
  
 1023 文字の長さの制限にも適用されます、完全修飾名の文字列全体など`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`です。  
  
 次の例では、有効な要素名を示します。  
  
 `aB123__45`  
  
 `_567`  
  
 次の例では、無効な要素名を示します。 最初にアンダー スコアのみが含まれています、2 つ目が 10 進数の数字で始まるおよび 3 番目に無効な文字 ($) が含まれています。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  アンダー スコアで始まる要素名 (`_`) に含まれていませんが、[言語非依存および言語非依存コンポーネント](../../../../standard/language-independence-and-language-independent-components.md)(CLS) ため、CLS 準拠コードのような名前を定義するコンポーネントを使用することはできません。 ただし、要素名は、他の場所内でアンダー スコアは CLS に準拠していません。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、自分の名前する必要がありますをできるだけ短く中の要素の特性を明確にします。 これにより、コードの読みやすさを向上させ、行の長さとソース ファイルのサイズを削減できます。  
  
 その一方で、自分の名前を記述しません。 適切にどのような要素を表し、コードがそれを使用する方法長さである必要があります。 これは、コードの読みやすくするため重要です。 理解しようとしている他の人が自分で見ることが、作成した後に長時間場合や、適切な要素名は、かなりの時間を保存できます。  
  
## <a name="escaped-names"></a>エスケープされた名前  
 一般に、要素名は、する必要がありますと一致しませんなどの Visual Basic で予約されているキーワードのいずれかの`Case`または`Friend`です。 ただし、定義することができます、*エスケープ名前*、角かっこで囲まれている (`[ ]`)。 エスケープされた名前は、角かっこは、任意のあいまいさをなくすために、Visual Basic のキーワードに一致することができます。 また、後続のコードで、名前を参照するときに、角かっこを使用します。  
  
 一般に、エスケープされた名前を使用する必要がありますされる場合にのみ。  
  
-   コードは、名前として使用されているキーワードが確保されていない Visual Basic の以前のバージョンから移行しました。または  
  
-   指定されたキーワードが予約されていない別の言語で記述されたコードを使用しています。  
  
 それ以外の場合、キーワードを使用してその名前が競合する場合、要素名の変更を検討してください。 統合開発環境 (IDE) では、これを行う簡単な方法を提供します。 詳細については、次を参照してください。[リファクタリング](/visualstudio/vb-ide/refactoring-vb)です。  
  
## <a name="case-sensitivity-in-names"></a>名前で大文字小文字の区別  
 Visual Basic での要素名は区別されません。 これは、コンパイラは、大文字と小文字のみが異なる 2 つの名前を比較し、ときを解釈するには同じ名前としてことを意味します。 たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 ただし、共通言語ランタイム (CLR) は、大文字小文字を区別バインディングを使用します。 このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。 たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。 かどうか、その後、クラスを再コンパイルし、変更する要素の名前を`abc`クラスを使用して、他のアセンブリではその要素がアクセスできなく可能性があります。 したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。  
  
## <a name="names-and-locales"></a>名前とロケール  
 名前の比較は、ロケールに依存しません。 1 つのロケールで 2 つの名前が同じ場合は、すべてのロケールに一致するように保証されます。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
