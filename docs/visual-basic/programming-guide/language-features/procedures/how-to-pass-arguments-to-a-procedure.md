---
title: "方法: プロシージャ (Visual Basic) に引数を渡す |Microsoft ドキュメント"
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ddccd476b2347368d0435f637edf3882db306f45
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>方法: プロシージャに引数を渡す (Visual Basic)
プロシージャを呼び出すときに、かっこで囲まれた引数リストを持つプロシージャ名に従います。 プロシージャに定義されたすべての必須パラメーターに対応する引数を指定して、オプションで、引数を指定することができます、`Optional`パラメーター。 指定しない場合、`Optional`呼び出しのパラメーターは、すべての後続の引数を指定している場合、引数リスト内の場所をマークするコンマを含める必要があります。  
  
 など、対応するパラメーターと異なるに渡すには、データ型の引数にするかどうかに`Byte`に`String`、型チェック スイッチを設定することができます ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) に`Off`します。 場合`Option Strict`は`On`、いずれかを使用する必要があります変換または変換の明示的なキーワードを拡大します。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)します。  
  
 詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)します。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>プロシージャに&1; つまたは複数の引数を渡す  
  
1.  呼び出し元のステートメント、プロシージャ名にかっこに従います。  
  
2.  かっこの内側には、引数リストを配置します。 プロシージャに定義された各必須パラメーターの引数が含まれ、引数はコンマで区切ります。  
  
3.  それぞれの引数は、対応するパラメーターの型、プロシージャに変換できるデータ型に評価される有効な式を定義することを確認します。  
  
4.  パラメーターとして定義されている場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)、引数リストに含めるか、この句を省略することができます。 句を省略した場合は、そのパラメーターに定義された既定値が使用されます。  
  
5.  引数を省略した場合、`Optional`パラメーターとパラメーター リストで別のパラメーター後に、省略されている引数の位置をマークするには、引数リスト内の余分なコンマにします。  
  
     次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。  
  
     [!code-vb[VbVbcnProcedures #&34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     前の例では、必要な最初の引数は表示されるメッセージ文字列を提供します。 メッセージ ボックスに表示するボタンを指定する省略可能な第&2; パラメーターの引数を省略します。 呼び出しは、値を指定していないため`MsgBox`が既定値を使用`MsgBoxStyle.OKOnly`、のみが表示されますが、 **ok**  ボタンをクリックします。  
  
     引数リストで、2 つ目のコンマは省略すると&2; 番目の引数の場所をマークし、最後の文字列は省略可能な&3; 番目のパラメーターに渡される`MsgBox`、これは、タイトル バーに表示されるテキスト。  
  
## <a name="see-also"></a>関連項目  
 [Sub プロシージャ](./sub-procedures.md)   
 [Function プロシージャ](./function-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [方法: プロシージャのパラメーターを定義します。](./how-to-define-a-parameter-for-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [再帰プロシージャ](./recursive-procedures.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
