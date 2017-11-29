---
title: "Mid ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61d812ef91acc65728b04efc9aa99e3975e71d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
 必須です。 `Integer`式。 文字の位置`Target`テキストの置換を開始します。 `Start`1 から始まるインデックスを使用します。  
  
 `Length`  
 省略可能です。 `Integer`式。 置換する文字の数。 省略した場合、すべての`String`を使用します。  
  
 `StringExpression`  
 必須です。 `String`式の一部を置換する`Target`です。  
  
## <a name="exceptions"></a>例外  
  
|例外の種類|状態|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 または`Length`< 0 です。|  
  
## <a name="remarks"></a>コメント  
 置換される文字数は、の文字数以下では常に`Target`です。  
  
 Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A>関数と`Mid`ステートメントです。 この要素はどちらも、文字列の文字の指定された数が、`Mid`関数の中に文字を返します、`Mid`文字をステートメントに置き換えます。 詳細については、「<xref:Microsoft.VisualBasic.Strings.Mid%2A>」を参照してください。  
  
> [!NOTE]
>  `MidB`以前のバージョンの Visual Basic のステートメントには文字ではなく、(バイト単位) 内の部分文字列が置き換えられます。 2 バイト文字セット (DBCS) のアプリケーションで文字列を変換するため、主に使用されます。 Unicode では、すべての Visual Basic の文字列と`MidB`は現在サポートされていません。  
  
## <a name="example"></a>例  
 この例では、`Mid`ステートメントに指定した文字列変数の文字数を別の文字列から文字に置き換えます。  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:**`Strings`  
  
 **アセンブリ:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Visual Basic の文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
