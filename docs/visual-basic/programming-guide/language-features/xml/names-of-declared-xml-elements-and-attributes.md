---
title: "宣言する XML 要素と属性の名前 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣言する XML 要素と属性の名前 (Visual Basic)
このトピックでは[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルの XML 要素および属性の名前付けのガイドライン。  XML リテラルでは、ローカル名または修飾名を指定できます。 XML 名前空間プレフィックス、コロン、およびローカル名の修飾名で構成されます。 XML 名前空間プレフィックスの詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。  
  
## <a name="rules"></a>ルール  
 要素または属性のローカル名[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]次の規則に従う必要があります。  
  
-   名前空間を開始します。 英文字またはアンダー スコアで始める必要があります (`_`)。  
  
-   それだけアルファベット文字、10 進数字、アンダー スコア、ピリオド (.)、およびハイフンを含める必要があります (-)。  
  
-   1024 を超える数の文字はできません。  
  
-   名前に含まれるコロンは、名前空間の区切りを示します。 したがって、特定の名前の XML 名前空間を指定するだけのコロンを使用できます。  
  
 さらに、次のガイドラインに従う必要があります。  
  
-   XML 1.0 仕様では、大文字と小文字バリエーションの 1 つの"xml"、文字列で始まるすべての名前を予約します。 したがって、これらの要素名および属性名は使用しないでください。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、名前する必要がありますをできるだけ短く中の要素の特性を明確にします。 これにより、コードの読みやすさを向上させ、行の長さとソース ファイルのサイズを削減できます。  
  
 ただし、自分の名前は、長さを適切に記述しません要素またはコードがそれを使用する方法である必要があります。 これは、コードの読みやすくするため重要です。 理解しようとしている他の人が自分で見ることが、作成した後に長時間場合や、適切な要素名は、時間を節約できます。  
  
## <a name="case-sensitivity-in-names"></a>名前で大文字小文字の区別  
 XML 要素の名前は大文字小文字を区別します。 つまり、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラがアルファベットの大文字小文字のみが異なる 2 つの名前を比較し、異なる名前として解釈します。 たとえば、解釈`ABC`と`abc`要素を区切るを参照するとします。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 XML 要素リテラルを作成する場合は、要素名の XML 名前空間プレフィックスを指定できます。 詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
