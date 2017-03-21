---
title: "Mid ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e385d6838daa16d45903c6b270fc47ad88797845
ms.lasthandoff: 03/13/2017

---
# <a name="mid-statement"></a>Mid ステートメント
指定した数の文字を置換、`String`別の文字列から文字を含む変数。  
  
## <a name="syntax"></a>構文  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>指定項目  
 `Target`  
 必須です。 名前、`String`変数を変更します。  
  
 `Start`  
 必須です。 `Integer`式。 文字の位置`Target`テキストの置換が開始します。 `Start`1 から始まるインデックスを使用します。  
  
 `Length`  
 省略可能です。 `Integer`式。 置換する文字の数。 省略した場合、すべての`String`を使用します。  
  
 `StringExpression`  
 必須です。 `String`式の一部を置換する`Target`です。  
  
## <a name="exceptions"></a>例外  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException></xref:System.ArgumentException>|`Start`<= 0="" or=""></=>`Length`< 0.></ 0.>|  
  
## <a name="remarks"></a>コメント  
 置き換えられた文字の数は、文字数以下では常に`Target`します。  
  
 Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A>関数と`Mid`ステートメント</xref:Microsoft.VisualBasic.Strings.Mid%2A>。 この要素はどちらも、文字列内の文字の指定の数が、`Mid`関数の中に文字を返します、`Mid`文字をステートメントに置き換えます。 詳細については、 <xref:Microsoft.VisualBasic.Strings.Mid%2A>。</xref:Microsoft.VisualBasic.Strings.Mid%2A>を参照してください。  
  
> [!NOTE]
>  `MidB`以前のバージョンの Visual Basic のステートメントには、文字ではなく、(バイト単位) の部分文字列が置き換えられます。 2 バイト文字セット (DBCS) のアプリケーションで文字列に変換するためには、主に使用されます。 Visual Basic のすべての文字列が Unicode と`MidB`現在サポートされていません。  
  
## <a name="example"></a>例  
 この例では、`Mid`ステートメントに指定した文字列変数の文字数を別の文字列から文字に置き換えます。  
  
 [!code-vb[VbVbalrStrings&#5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:**`Strings`  
  
 **アセンブリ:**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Visual Basic における文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
