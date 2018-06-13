---
title: '方法: プロパティを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 6e3faed9880b6417f17ab8fe84bc5162e803c437
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656244"
---
# <a name="how-to-create-a-property-visual-basic"></a>方法: プロパティを作成する (Visual Basic)
プロパティの定義の間で囲む必要が、`Property`ステートメントおよび`End Property`ステートメントです。 この定義内で定義する、`Get`プロシージャ、`Set`プロシージャ、またはその両方です。 すべてのプロパティのコードの範囲内でこれらのプロシージャです。  
  
 `Get`プロシージャ、プロパティの値を取得し、`Set`プロシージャが値を格納します。 プロパティを読み取り/書き込みアクセス権がある場合は、どちらの手順を定義する必要があります。 読み取り専用のプロパティを定義するのみ`Get`、書き込み専用のプロパティを定義するのみと`Set`です。  
  
### <a name="to-create-a-property"></a>プロパティを作成するには  
  
1.  任意のプロパティまたはプロシージャを使用して、外部を使用して、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)」と入力し、`End Property`ステートメントです。  
  
2.  次のプロパティは、パラメーターを受け取る場合、`Property`パラメーター リストをかっこで、プロシージャの名前を持つキーワード。  
  
3.  かっこの後に、`As`句をプロパティの値のデータ型を指定します。 書き込み専用プロパティにもデータ型を指定する必要があります。  
  
4.  追加`Get`と`Set`プロシージャに、必要に応じて。 次の手順を参照してください。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>プロパティ値を取得する Get プロシージャを作成するには  
  
1.  間、`Property`と`End Property`ステートメント、書き込み、 [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)」と入力し、`End Get`ステートメントです。 パラメーターを定義する必要はありません、`Get`プロシージャです。  
  
2.  間で、プロパティの値を取得するコードのステートメントを配置、`Get`と`End Get`ステートメントです。 その他の計算やデータ操作を生成して、プロパティの値を返すだけでなく、このコードを含めることができます。  
  
3.  使用して、`Return`ステートメントを呼び出し元のコードに、プロパティの値を返します。  
  
 記述する必要があります、`Get`プロシージャおよび読み取り専用プロパティの読み取り/書き込みプロパティです。 定義する必要はありません、`Get`書き込み専用プロパティ プロシージャをします。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>プロパティの値を書き込みますセット プロシージャを作成するには  
  
1.  間、`Property`と`End Property`ステートメント、書き込み、 [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)」と入力し、`End Set`ステートメントです。  
  
2.  `Set`ステートメントでは、以下の`Set`パラメーター リストをかっこで囲まれたキーワード。 このパラメーターの一覧には、呼び出し元のコードで渡された値の値には、少なくともを持つパラメーターを含める必要があります。 この値パラメーターの既定の名前は`Value`、該当する場合は、別の名前を使用することができます。 Value パラメーターと同じデータ型、プロパティ自体が必要です。  
  
3.  間でプロパティに値を格納するコードのステートメントを配置、`Set`と`End Set`ステートメントです。 このコードは、その他の計算や検査して、プロパティの値を格納するだけでなくデータの操作を含めることができます。  
  
4.  Value パラメーターを使用して、呼び出し元のコードで指定した値をそのまま使用します。 代入ステートメント内で直接この値を格納するかを格納する内部値を計算する式で使用します。  
  
 記述する必要があります、`Set`プロシージャ読み取り/書き込みプロパティおよび書き込み専用プロパティです。 定義する必要はありません、`Set`読み取り専用プロパティ プロシージャをします。  
  
## <a name="example"></a>例  
 次の例では、2 つの構成名、名、姓と名と完全名を格納する読み取り/書き込みプロパティを作成します。 呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは次の 2 つの構成名を結合し、完全な名前を返します。 呼び出し元のコードは、新しい完全な名前を割り当てを行うとき、`Set`プロシージャを次の 2 つの部分に分割しようとしました。 場所が見つからない場合、名前としてすべて格納します。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 次の例では、通常、プロパティ プロシージャ呼び出しの`fullName`します。 最初の呼び出しは、プロパティ値を設定し、2 番目の呼び出しでは、それを取得します。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
