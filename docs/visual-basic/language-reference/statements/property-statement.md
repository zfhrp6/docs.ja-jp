---
title: "Property Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.PropertySet"
  - "vb.Property"
  - "vb.PropertyGet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Property ステートメント"
  - "既定の修飾子"
  - "プロパティ プロシージャ、プロパティをステートメント"
  - "Property キーワード"
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
caps.handback.revision: 41
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティの名前、およびプロパティの値を格納して取得するために使用されるプロパティ プロシージャを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     省略可能です。 このプロパティに適用される属性の一覧または `Get` または `Set` プロシージャです。 参照してください [属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
-   `Default`  
  
     省略可能です。 このプロパティは、クラスまたは構造体が定義されている既定のプロパティを指定します。 既定のプロパティのパラメーターを受け入れる必要がありに設定してプロパティ名を指定しなくても取得します。 としてプロパティを宣言する場合は、 `Default`, 、使用することはできません `Private` プロパティまたはプロパティ プロシージャのいずれかです。  
  
-   `accessmodifier`  
  
     [省略可能な `Property` ステートメントの 1 つだけで、 `Get` と `Set` ステートメントです。 次のいずれかの値を指定します。  
  
    -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     「 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
-   `propertymodifiers`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [オーバーライド](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [オーバーライド可能です](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     省略可能です。 参照してください [共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください [シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `ReadOnly`  
  
     省略可能です。 参照してください [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
-   `WriteOnly`  
  
     省略可能です。 参照してください [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)します。  
  
-   `Iterator`  
  
     省略可能です。 参照してください [反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
-   `name`  
  
     必須です。 プロパティ名。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
-   `parameterlist`  
  
     省略可能です。 このプロパティのパラメーターとの可能な追加パラメーターを表すローカル変数名の一覧、 `Set` プロシージャです。 参照してください [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。  
  
-   `returntype`  
  
     必要な場合 `Option``Strict` は `On`です。 このプロパティによって返される値のデータ型。  
  
-   `Implements`  
  
     省略可能です。 このプロパティには、このプロパティを含むクラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつ、1 つまたは複数のプロパティが実装していることを示します。 参照してください [ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)します。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装されているプロパティの一覧。  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     `implementedproperty` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |||  
    |-|-|  
    |パーツ|説明|  
    |`interface`|必須です。 このプロパティによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。|  
    |`definedname`|必須です。 名前のプロパティを定義する `interface`です。|  
  
-   `Get`  
  
     省略可能です。 プロパティがマークされているかどうかに必要な `WriteOnly`です。 開始、 `Get` プロパティの値を返すために使用するプロパティ プロシージャです。  
  
-   `statements`  
  
     省略可能です。 内で実行するステートメントのブロック、 `Get` または `Set` プロシージャです。  
  
-   `End Get`  
  
     終了、 `Get` プロパティ プロシージャです。  
  
-   `Set`  
  
     省略可能です。 プロパティがマークされているかどうかに必要な `ReadOnly`です。 開始、 `Set` プロパティ プロシージャ、プロパティの値を格納するために使用します。  
  
-   `End Set`  
  
     終了、 `Set` プロパティ プロシージャです。  
  
-   `End Property`  
  
     このプロパティの定義を終了します。  
  
## <a name="remarks"></a>コメント  
  `Property` ステートメントは、プロパティの宣言を導入します。 プロパティがあることができます、 `Get` プロシージャ (読み取り専用)、 `Set` プロシージャ (書き込み専用)、または両方 (読み取り/書き込み)。 省略することができます、 `Get` と `Set` プロシージャは、自動実装プロパティを使用する場合。 詳細については、次を参照してください。 [Auto-Implemented プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)します。  
  
 使用する `Property` クラス レベルでのみです。 つまり、 *宣言コンテキスト* プロパティは、クラス、構造体、モジュール、またはインターフェイスである必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、次を参照してください。 [宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。  
  
 既定では、プロパティは、パブリック アクセスを使用します。 アクセス修飾子を使って、このプロパティのアクセス レベルを調整することができます、 `Property` ステートメント、および、必要に応じて調整できますより制限の厳しいアクセス レベルは、プロパティ プロシージャのいずれかです。  
  
 Visual Basic のパラメーターを渡す、 `Set` プロパティを設定中にプロシージャです。 パラメーターを指定しない場合 `Set`, 、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して `value`します。 このパラメーターは、プロパティに割り当てられる値を保持します。 通常、この値は、プライベートなローカル変数に格納およびそれを返すときに、 `Get` プロシージャが呼び出されます。  
  
## <a name="rules"></a>ルール  
  
-   **混合アクセス レベル。** 必要に応じていずれかの異なるアクセス レベルを指定することができます読み取り/書き込みプロパティを定義する場合、 `Get` または `Set` プロシージャが、どちらかです。 これを行うと、プロシージャのアクセス レベルが、プロパティのアクセスのレベル以上に制限する必要があります。 例では、このプロパティが宣言されている場合の `Friend`, 、宣言することができます、 `Set` プロシージャ `Private`, 、ではなく `Public`です。  
  
     定義する場合は、 `ReadOnly` または `WriteOnly` プロパティ、1 つのプロパティのプロシージャ (`Get` または `Set`, 、それぞれ) すべてのプロパティを表します。 プロパティの 2 つのアクセス レベルを設定することがあるために、このような手順は、異なるアクセス レベルを宣言できません。  
  
-   **型を返します。**  `Property` ステートメントで返される値のデータ型を宣言できます。 任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。  
  
     指定しない場合 `returntype`, 、プロパティの戻り値を `Object`します。  
  
-   **実装です。** このプロパティで使用する場合、 `Implements` キーワードを含むクラスまたは構造体が必要、 `Implements` 直後のステートメントの `Class` または `Structure` ステートメントです。  `Implements` ステートメントで指定された各インターフェイスを含める必要があります `implementslist`します。 ただし、インターフェイスを定義する名前、 `Property` (で `definedname`) すると、このプロパティの名前と同じである必要はありません (で `name`)。  
  
## <a name="behavior"></a>動作  
  
-   **プロパティ プロシージャから取得します。** ときに、 `Get` または `Set` 、それを呼び出し元ステートメントの次のステートメントと、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
      `Exit Property` と `Return` ステートメントでは、プロパティ プロシージャからすぐに終了します。 任意の数の `Exit Property` と `Return` ステートメントが任意の場所で、手順と混在させることが `Exit Property` と `Return` ステートメントです。  
  
-   **値を返します。** 値を返す、 `Get` プロシージャ、プロパティ名に値を割り当てるか、含めることで、 `Return` ステートメントです。 次の例では、戻り値を割り当てて、プロパティ名に `quoteForTheDay` し、使用して、 `Exit Property` を返すステートメントです。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     使用する場合 `Exit Property` 値を割り当てることがなく `name`, 、 `Get` プロシージャは、このプロパティのデータ型の既定値を返します。  
  
      `Return` 同時ステートメントは、代入、 `Get` プロシージャを返す値し、手順を終了します。 次の例に示します。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、クラスのプロパティを宣言します。  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [自動実装プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)   
 [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [既定値](../../../visual-basic/language-reference/modifiers/default.md)