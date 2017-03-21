---
title: "宣言する XML 要素と属性 (Visual Basic) の名前。Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
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
ms.openlocfilehash: ed8ecf69170acf9745a4038975e7e3421722d52d
ms.lasthandoff: 03/13/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣言する XML 要素と属性の名前 (Visual Basic)
このトピックでは[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルの XML 要素および属性を名前付けのガイドラインです。  XML リテラルでは、ローカル名または修飾名を指定できます。 修飾名は、XML 名前空間プレフィックス、コロン、およびローカル名で構成されます。 XML 名前空間プレフィックスの詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。  
  
## <a name="rules"></a>ルール  
 要素または属性のローカル名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]次の規則に従う必要があります。  
  
-   名前空間がそれを開始できます。 英文字またはアンダー スコアで始まる必要があります (`_`)。  
  
-   のみ英文字、10 進数字、アンダー スコア、ピリオド (.)、およびハイフンを含める必要があります (-)。  
  
-   1,024 を超える文字はできません。  
  
-   名前に含まれるコロンは、名前空間の区切りを示します。 したがって、特定の名前の XML 名前空間を指定する場合のみ、コロンを使用できます。  
  
 さらに、次のガイドラインに従う必要があります。  
  
-   XML 1.0 仕様では、大文字と小文字のいずれかのバリエーションの"xml"を文字列で始まるすべての名前を予約します。 したがって、これらの要素名および属性名は使用しないでください。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、名前する必要がありますできるだけ短く中の要素の特性を明確にします。 これにより、コードの読みやすさを向上し、行の長さとソース ファイルのサイズを小さきます。  
  
 ただし、自分の名前は、長さいない適切に記述できる要素かどうか、コードがこれを使用する方法である必要があります。 これは、コードの読みやすさにとって重要です。 使い方も理解しようとする他の人がいる場合、または自分で検索する場合に作成した後、長い時間は、適切な要素の名前は、時間を節約できます。  
  
## <a name="case-sensitivity-in-names"></a>名前に大文字小文字の区別  
 XML 要素名は、大文字小文字が区別されます。 つまり、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラがアルファベットの大文字小文字の表記が異なる&2; つの名前を比較し、異なる名前として解釈します。 たとえば、解釈`ABC`と`abc`要素を区切る参照するものとします。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 XML 要素リテラルを作成する場合は、要素名の XML 名前空間プレフィックスを指定できます。 詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
