---
title: '方法: 複数のアクセス レベルを持つプロパティを宣言する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 8d25086fe6f8b5f5300006466ef49782cb065edf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651412"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>方法: 複数のアクセス レベルを持つプロパティを宣言する (Visual Basic)
場合は、`Get`と`Set`手順異なるアクセス レベルを設定するプロパティについてでさらに小さくレベルを使用することができます、`Property`ステートメントといずれかより制限の厳しいレベル、`Get`または`Set`ステートメント。 プロパティの値を取得することができるコードの特定の部分と値を変更することができるコードの他の特定部分したい場合は、プロパティに混合アクセス レベルを使用します。  
  
 アクセス レベルの詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>混合アクセス レベルを持つプロパティを宣言するには  
  
1.  通常の方法でプロパティを宣言し、制限の緩いアクセス レベルを指定します (など`Public`) で、`Property`ステートメントです。  
  
2.  宣言するか、`Get`または`Set`より制限の厳しいアクセス レベルを指定する手順 (など`Friend`)。  
  
3.  その他のプロパティ プロシージャでは、アクセス レベルを指定しません。 宣言されているアクセス レベルを想定しています、`Property`ステートメントです。 プロパティ プロシージャの 1 つのみにアクセスを制限することができます。  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     前の例で、`Get`手順では、同じ`Protected`自体のプロパティとしてアクセス中に、`Set`手順では`Private`アクセスします。 派生したクラス`employee`読み取ることができます、`salary`値しか、`employee`クラスで設定できます。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
