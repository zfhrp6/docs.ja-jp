---
title: Property プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656088"
---
# <a name="property-procedures-visual-basic"></a>Property プロシージャ (Visual Basic)
プロパティ プロシージャは、一連のモジュール、クラスまたは構造体のカスタム プロパティを操作する Visual Basic ステートメントです。 プロパティ プロシージャとも呼ばれます*プロパティ アクセサー*です。  
  
 Visual Basic は、次のプロパティ プロシージャについて説明します。  
  
-   A`Get`プロシージャ、プロパティの値を返します。 式でプロパティにアクセスするときに呼び出されます。  
  
-   A`Set`プロシージャ、プロパティのオブジェクト参照を含め、値を設定します。 プロパティの値を代入するときに呼び出されます。  
  
 使用して、対で通常プロパティ プロシージャを定義する、`Get`と`Set`がステートメントを定義できますいずれかの手順を単独でプロパティが読み取り専用の場合 ([Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)) または書き込み専用 ([設定ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md))。  
  
 省略することができます、`Get`と`Set`自動実装プロパティを使用する場合、そのプロシージャです。 詳細については、「[自動実装プロパティ](./auto-implemented-properties.md)」を参照してください。  
  
 プロパティは、クラス、構造体、およびモジュールで定義できます。 プロパティは、`Public`既定では、つまり、どこからでも呼び出すことができます、プロパティのコンテナーにアクセスできるアプリケーションでします。  
  
 プロパティと変数の比較を参照してください。[プロパティ間の相違点と Visual Basic における変数](./differences-between-properties-and-variables.md)です。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 プロパティ自体が囲まれたコードのブロックで定義されている、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。 このブロック内で各プロパティ プロシージャは、宣言ステートメントで囲まれた内部ブロックとして表示されます。 (`Get`または`Set`) と一致する、`End`宣言します。  
  
 プロパティと、プロシージャの宣言の構文は次のとおりです。  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers`を指定できますアクセス レベルおよびシャドウ、および、オーバーライド、共有、オーバー ロードに関する情報も、プロパティは、読み取り専用または書き込み専用かどうか。 `AccessLevel`上、`Get`または`Set`プロシージャは、プロパティ自体に指定されたアクセス レベルより限定的な任意のレベルを指定できます。 詳細については、次を参照してください。 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)です。  
  
### <a name="data-type"></a>データの種類  
 プロパティのデータ型およびプリンシパルのアクセス レベルがで定義されている、`Property`ステートメントでは、プロパティ プロシージャではなく、します。 プロパティは、1 つだけのデータ型を持つことができます。 たとえば、格納するプロパティを定義することはできません、`Decimal`値しますが、取得、`Double`値。  
  
### <a name="access-level"></a>アクセス レベル  
 ただし、プロパティのプリンシパルのアクセス レベルを定義し、さらに、プロパティ プロシージャのいずれかでアクセス レベルを制限できます。 たとえば、定義することができます、`Public`プロパティし、定義、`Private Set`プロシージャです。 `Get`プロシージャまま`Public`です。 プロパティのプロシージャの 1 つに、アクセス レベルを変更することができすることができますのみがプリンシパルのアクセス レベルよりも制限します。 詳細については、次を参照してください。[する方法: 混合アクセス レベルを持つプロパティを宣言](./how-to-declare-a-property-with-mixed-access-levels.md)です。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 各パラメーターを宣言すると、同様の操作を行う[Sub プロシージャ](./sub-procedures.md)引き渡し方法がある点を除いて、`ByVal`です。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 パラメーターが省略可能な場合は、宣言の一部として既定値も指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>プロパティ値  
 `Get`プロシージャ、戻り値がプロパティの値として呼び出し元の式を指定します。  
  
 `Set`プロシージャ、新しいプロパティ値は、のパラメーターに渡される、`Set`ステートメントです。 パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。 コンパイラが暗黙的なパラメーターを使用して、パラメーターを宣言していない場合`Value`をプロパティに割り当てられる新しい値を表します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 プロパティ プロシージャをプロパティに参照することによって暗黙的を呼び出すとします。 使用するプロパティの名前、変数の名前を使用すると同じ方法は、省略できないすべての引数の値を指定する必要がある点を除いて、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。  
  
 暗黙的な呼び出しの構文、`Set`手順のとおりです。  
  
 `propertyname[(argumentlist)] = expression`  
  
 暗黙的な呼び出しの構文、`Get`手順のとおりです。  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次のプロパティは、2 つの構成名、名、姓と名として完全な名前を格納します。 呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは次の 2 つの構成名を結合し、完全な名前を返します。 呼び出し元のコードは、新しい完全な名前を割り当てを行うとき、`Set`プロシージャを次の 2 つの部分に分割しようとしました。 場所が見つからない場合、名前としてすべて格納します。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 次の例では、通常、プロパティ プロシージャ呼び出しの`fullName`します。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Function プロシージャ](./function-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
