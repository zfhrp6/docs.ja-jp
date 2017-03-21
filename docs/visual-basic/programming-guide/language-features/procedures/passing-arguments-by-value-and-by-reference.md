---
title: "引数値渡しと参照渡し (Visual Basic) |Microsoft ドキュメント"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 56d1ceba14020ca7f3dc750c2318efd3e9586af0
ms.lasthandoff: 03/13/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡し (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、プロシージャに引数を渡すことができます*値によって*または*参照によって*します。 これと呼ばれますが、*渡す機能*、し、プロシージャが呼び出し元のコードで引数を基になるプログラミングの要素を変更するかどうかを決定します。 プロシージャの宣言では、各パラメーターの引き渡し方法を決定を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワードです。  
  
## <a name="distinctions"></a>相違点  
 プロシージャに引数を渡す場合は、相互にやり取りするいくつかの違いに注意してください。  
  
-   基になるプログラミング要素は、変更可能または変更できないかどうか  
  
-   引数自体が変更可能または変更不可能なのかどうか  
  
-   値渡しまたは参照渡しの引数が渡されるかどうか  
  
-   引数のデータ型は、値型または参照型かどうか  
  
 詳細については、次を参照してください。[変更間の相違点と変更できない引数](./differences-between-modifiable-and-nonmodifiable-arguments.md)と[の相違点の間の値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)します。  
  
## <a name="choice-of-passing-mechanism"></a>渡す機能の選択  
 慎重に各引数の引き渡し方法を選択する必要があります。  
  
-   **保護**します。 引数を渡す方法を選択すると、最も重要な条件を変更する変数を呼び出すことのリスクです。 引数を渡す場合の利点`ByRef`はプロシージャがその引数を通じて呼び出し元コードに値を返すことができます。 引数を渡す場合の利点`ByVal`からプロシージャによって変更されている変数を防ぐことができます。  
  
-   **パフォーマンス**します。 引数渡しの方法が、コードのパフォーマンスに影響を与えることができますが、違いは一般にごくわずかです。 唯一の例外が渡される値型`ByVal`します。 この場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]引数のデータ全体の内容をコピーします。 そのため、構造体などの大きな値型場合がこれを渡す方が効率的`ByRef`します。  
  
     参照型でデータへのポインターにのみ、コピーした (4 バイト プラットフォームでは 32 ビット、64 ビット プラットフォームでは 8 バイト) です。 そのため、型の引数を渡すことができます`String`または`Object`パフォーマンスを損なわずに値渡しされます。  
  
## <a name="determination-of-the-passing-mechanism"></a>引数渡しの方法の決定  
 プロシージャの宣言では、各パラメーターの引き渡し方法を指定します。 呼び出し元のコードを上書きできません、`ByVal`メカニズムです。  
  
 パラメーターが宣言されている場合`ByRef`、呼び出し元のコードにするメカニズムを強制できます`ByVal`引数の名前を呼び出しでは、かっこで囲みます。 詳細については、次を参照してください。[方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。  
  
 既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。  
  
## <a name="when-to-pass-an-argument-by-value"></a>引数の値渡しする場合  
  
-   引数の基になる呼び出し元のコード要素が変更不可能な要素の場合は、対応するパラメーターを宣言[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。 変更不可能な要素の値に変更できるコードはありません。  
  
-   基になる要素が変更可能をその値を変更できるようにする手順をしたくない場合に、パラメーター宣言`ByVal`します。 呼び出し元のコードだけでは、値によって渡される変更可能な要素の値を変更できます。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>引数は参照渡しする場合  
  
-   プロシージャの呼び出し元のコードで基になる要素を変更する必要が本当の場合は、対応するパラメーターを宣言[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。  
  
-   コードの適切な実行は、呼び出し元のコード内の基になる要素を変更するプロシージャに依存している場合に、パラメーター宣言`ByRef`します。 値で渡す場合、または呼び出し元のコードをオーバーライドする場合、`ByRef`渡す引数をかっこで囲んで機能プロシージャの呼び出しが予期しない結果を生じる可能性があります。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、引数を値渡しする場合と参照渡しする場合を示します。 プロシージャ`Calculate`が両方とも、`ByVal`と`ByRef`パラメーター。 金利、指定された`rate`、および合計金額、 `debt`、プロシージャの作業は、新しい値を計算する`debt`の元の値を金利を適用した結果は`debt`です。 `debt`は、`ByRef`パラメーター、呼び出し元のコードに対応する引数の値に新しい合計が反映されます`debt`します。 パラメーター`rate`は、`ByVal`パラメーターのため`Calculate`の値を変更しないでください。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnProcedures #&74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)   
 [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
