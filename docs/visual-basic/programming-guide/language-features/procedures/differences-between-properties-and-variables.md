---
title: Visual Basic のプロパティと変数の違い
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 126e4baa2752ba7ccb5e8ff7b06a44839c1d0af2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651506"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic のプロパティと変数の違い
変数とプロパティは、アクセス可能な値を表します。 ただし、これには記憶域および実装内の違いがあります。  
  
## <a name="variables"></a>変数  
 A*変数*メモリ位置に直接対応しています。 1 つの宣言ステートメントで変数を定義するとします。 変数を指定できます、*ローカル変数*、そのプロシージャ内でのみ使用し、プロシージャ内に定義することもできます、*メンバー変数*、いずれかの内部ではなく、モジュール、クラスまたは構造体で定義されています。プロシージャです。 メンバー変数とも呼ばれますが、*フィールド*です。  
  
## <a name="properties"></a>プロパティ  
 A*プロパティ*はモジュール、クラスまたは構造体で定義されているデータ要素です。 間でコード ブロックがプロパティを定義する、`Property`と`End Property`ステートメントです。 コード ブロックが含まれる、`Get`プロシージャ、`Set`プロシージャ、またはその両方です。 これらのプロシージャ*プロパティ プロシージャ*または*プロパティ アクセサー*です。 取得したり、プロパティの値を格納したりするには、に加えてアクセス カウンターの更新などのカスタム アクションを実行することもできます。  
  
## <a name="differences"></a>相違点  
 次の表は、変数とプロパティの重要な相違を示します。  
  
|異なる点|変数|プロパティ|  
|-------------------------|--------------|--------------|  
|宣言|1 つの宣言ステートメント|一連のコード ブロック内のステートメント|  
|実装|1 つの記憶域の場所|実行可能コード (プロパティ プロシージャ)|  
|記憶域|変数の値に直接関連付けられています。|通常、プロパティの親クラスまたはモジュールの外部からアクセスできない内部ストレージには<br /><br /> プロパティの値がありますまたはとして格納された要素が存在しない<sup>1</sup>|  
|実行可能コード|なし|少なくとも 1 つの手順があります。|  
|読み取りおよび書き込みアクセス|読み取り/書き込みまたは読み取り専用|読み取り/書き込み、書き込み専用または読み取り専用|  
|カスタムの動作 (に加えてを受け入れるかまたは値を返す)|無理です|設定またはプロパティの値を取得するの一部として実行されることができます。|  
  
 <sup>1</sup>変数とは異なり、プロパティの値は記憶域の単一の項目に直接対応しない可能性があります。 記憶域は利便性や、セキュリティの断片に分割することがまたは暗号化された形式で、値を格納する可能性があります。 このような場合、`Get`プロシージャはコンポーネントの編成または、格納された値の暗号化を解除し、`Set`プロシージャは、新しい値を暗号化またはストレージに分割します。 プロパティの値がありますの時間帯と同様に、一時的な場合、`Get`プロシージャが自動的に計算される、実行時にプロパティにアクセスするたびにします。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
