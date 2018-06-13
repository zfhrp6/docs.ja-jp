---
title: GetType 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603848"
---
# <a name="gettype-operator-visual-basic"></a>GetType 演算子 (Visual Basic)
返します、<xref:System.Type>指定した型のオブジェクト。 <xref:System.Type>オブジェクトなど、そのプロパティ、メソッド、およびイベントの種類に関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`typename`|情報を取得する型の名前。|  
  
## <a name="remarks"></a>コメント  
 `GetType`演算子を返します、 <xref:System.Type> 、指定されたオブジェクト`typename`です。 定義済みのすべての種類の名前を渡すことができます`typename`です。 次に例を示します。  
  
-   Visual Basic データ型など`Boolean`または`Date`です。  
  
-   .NET Framework クラス、構造体、モジュール、または、インターフェイスなど<xref:System.ArgumentException?displayProperty=nameWithType>または<xref:System.Double?displayProperty=nameWithType>です。  
  
-   クラス、構造体、モジュール、またはアプリケーションで定義されているインターフェイス。  
  
-   アプリケーションで定義されている任意の配列。  
  
-   アプリケーションで定義されている任意のデリゲート。  
  
-   Visual Basic、.NET Framework、またはアプリケーションによって定義された任意の列挙体です。  
  
 オブジェクト変数の型のオブジェクトを取得する場合は、使用、<xref:System.Type.GetType%2A?displayProperty=nameWithType>メソッドです。  
  
 `GetType`演算子は、次の状況で役に立ちます。  
  
-   型のメタデータは、実行時にアクセスする必要があります。 <xref:System.Type>オブジェクトは型のメンバーと配置の情報などのメタデータを提供します。 必要に、たとえば、アセンブリを反映するようになります。 詳細については、「<xref:System.Reflection?displayProperty=nameWithType>」を参照してください。  
  
-   同じ型のインスタンスを参照しているかどうかを次の 2 つのオブジェクト参照を比較するには。 場合は、`GetType`同じへの参照を返します<xref:System.Type>オブジェクト。  
  
## <a name="example"></a>例  
 次の例、`GetType`演算子を使用します。  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
