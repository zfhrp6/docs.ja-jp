---
title: "Property プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Set statement, Property procedures
- Visual Basic code, procedures
- return values, Property procedures
- syntax, Property procedures
- procedures, property
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], custom
- property procedures
- Get statement, property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
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
ms.openlocfilehash: f21d4c7d9bd8f14bbe7284bc08399e7ba6b466c3
ms.lasthandoff: 03/13/2017

---
# <a name="property-procedures-visual-basic"></a>Property プロシージャ (Visual Basic)
Property プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュール、クラスまたは構造体のカスタム プロパティを操作するステートメントです。 プロパティ プロシージャとも呼ばれます*プロパティ アクセサー*します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロパティの次の手順を示します。  
  
-   A`Get`プロパティの値を返します。 式の中でプロパティにアクセスするときに呼び出されます。  
  
-   A`Set`プロシージャ、プロパティのオブジェクト参照を含め、値を設定します。 プロパティの値を代入するときに呼び出されます。  
  
 使用して、ペアで通常プロパティ プロシージャを定義する、`Get`と`Set`プロパティが読み取り専用である場合は、ステートメントがからまたは編集手順だけでに定義することができます ([Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)) または書き込み専用 ([Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md))。  
  
 省略することができます、`Get`と`Set`プロシージャは、自動実装プロパティを使用する場合。 詳細については、次を参照してください。 [Auto-Implemented プロパティ](./auto-implemented-properties.md)します。  
  
 プロパティは、クラス、構造体、およびモジュールで定義できます。 プロパティは、`Public`既定では、つまりどこからでも呼び出すことが、プロパティのコンテナーにアクセスできるアプリケーションにします。  
  
 プロパティと変数の比較では、次を参照してください。[プロパティ間の相違点と Visual Basic における変数](./differences-between-properties-and-variables.md)します。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 プロパティ自体が囲まれたコードのブロックで定義されている、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。 宣言ステートメントで囲んだ内部ブロックとしてこのブロック内では各プロパティ プロシージャが表示されます (`Get`または`Set`) と、一致する`End`宣言します。  
  
 プロパティとそのプロシージャの宣言の構文は次のとおりです。  
  
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
  
 `Modifiers`を指定できますアクセス レベルと、オーバー ロード、オーバーライド、共有、およびシャドウに関する情報も、プロパティは、読み取り専用または書き込み専用かどうか。 `AccessLevel`上、`Get`または`Set`プロシージャは、プロパティ自体に対して指定されたアクセス レベルより限定的な任意のレベルを指定できます。 詳細については、次を参照してください。 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)します。  
  
### <a name="data-type"></a>データの種類  
 プロパティのデータ型とプリンシパルのアクセス レベルが定義されて、`Property`プロパティ プロシージャではなく、ステートメントです。 プロパティは、1 つだけのデータ型であることができます。 などを格納するプロパティを定義することはできません、`Decimal`値が、取得、`Double`値。  
  
### <a name="access-level"></a>アクセス レベル  
 ただし、プロパティのプリンシパルのアクセス レベルを定義し、さらに、プロパティ プロシージャのいずれかでアクセス レベルを制限できます。 たとえば、定義、`Public`プロパティし、定義、`Private Set`プロシージャです。 `Get`プロシージャまま`Public`します。 プロパティのプロシージャの&1; つに、アクセス レベルを変更することができます行いすることができますのみプリンシパルのアクセス レベル以上に制限します。 詳細については、次を参照してください。[方法: 混合アクセス レベルを持つプロパティを宣言](./how-to-declare-a-property-with-mixed-access-levels.md)します。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)渡すメカニズムである必要がありますが、`ByVal`です。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 パラメーターが省略可能な場合も、その宣言の一部として既定値を指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>プロパティ値  
 `Get`プロシージャの戻り値は、プロパティの値として呼び出し元の式に提供します。  
  
 `Set`プロシージャでは、新しいプロパティ値のパラメーターに渡される、`Set`ステートメントです。 パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。 コンパイラが暗黙の型のパラメーターを使用してパラメーターを宣言していない場合`Value`をプロパティに割り当てられる新しい値を表します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 プロパティ プロシージャは、プロパティを参照することによって暗黙的を呼び出します。 使用するプロパティの名前、変数の名前を使用すると同じ方法が、省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。  
  
 暗黙の呼び出しの構文、`Set`手順は、次のようにします。  
  
 `propertyname[(argumentlist)] = expression`  
  
 暗黙の呼び出しの構文、`Get`手順は、次のようにします。  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次のプロパティは、2 つの構成名、名、姓と名として完全な名前を格納します。 呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは、2 つの構成名を結合し、完全な名前を返します。 呼び出し元のコードが新しいの完全名を割り当てるときに、`Set`プロシージャを次の&2; つの部分に分割を試行します。 場所が見つからない場合は、すべてを最初の名前として格納します。  
  
 [!code-vb[VbVbcnProcedures&#8;](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 次の例では、一般的なプロシージャを呼び出して、プロパティの`fullName`です。  
  
 [!code-vb[VbVbcnProcedures&#9;](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Function プロシージャ](./function-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)   
 [方法: プロパティを作成します。](./how-to-create-a-property.md)   
 [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)   
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)   
 [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)   
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
