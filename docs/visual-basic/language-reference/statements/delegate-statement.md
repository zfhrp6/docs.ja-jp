---
title: Delegate ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 3965dc2d71ec9356cdb38d5ddcd4e00f9259951a
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234679"
---
# <a name="delegate-statement"></a>Delegate ステートメント
デリゲートを宣言するために使用します。 デリゲートは、参照型を参照する、`Shared`メソッド、型またはオブジェクトのインスタンス メソッドです。 このデリゲート クラスのインスタンスを作成するパラメーターと戻り値の型が一致するプロシージャを使用できます。 プロシージャし、後で呼び出せるデリゲート インスタンスの作成。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attrlist`|任意。 このデリゲートに適用される属性の一覧です。 複数の属性を指定するときは、コンマで区切ります。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。|  
|`accessmodifier`|任意。 どのようなコードからアクセスできるデリゲートを指定します。 次のいずれかの値を指定します。<br /><br /> - [パブリック](../../../visual-basic/language-reference/modifiers/public.md)です。 デリゲートを宣言した要素にアクセスするすべてのコードにアクセスできます。<br />-   [保護されている](../../../visual-basic/language-reference/modifiers/protected.md)です。 デリゲートのクラスまたは派生クラス内でコードにのみアクセスできます。<br />-   [フレンド](../../../visual-basic/language-reference/modifiers/friend.md)です。 デリゲートを同じアセンブリ内のコードのみにアクセスできます。<br />- [プライベート](../../../visual-basic/language-reference/modifiers/private.md)です。 デリゲートを宣言する要素内でコードからのみアクセスできます。<br /><br /> - [Protected Friend](../../language-reference/modifiers/protected-friend.md)のみ、デリゲートのクラス、派生クラスでは、または同じアセンブリ内のコードはデリゲートでアクセスできます。 <br />- [プライベート Protected](../../language-reference/modifiers/private-protected.md)だけコード、デリゲートのクラス内または同じアセンブリ内の派生クラスでは、デリゲートにアクセスできます。 |  
|`Shadows`|任意。 このデリゲートを宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされる要素のセットを非表示にすることを示します。 宣言された要素は、他の任意の種類の要素でシャドウできます。<br /><br /> シャドウされた要素は、その要素をシャドウする派生クラスからは使用できません。ただし、シャドウする要素がアクセスできない要素の場合は例外です。 たとえば場合、`Private`要素をシャドウする基本クラスの要素では、コードへのアクセス許可がない、`Private`要素は、基底クラス要素を代わりにアクセスします。|  
|`Sub`|省略可能、ただしか`Sub`または`Function`表示する必要があります。 代理人としてこのプロシージャを宣言`Sub`値を返さないプロシージャです。|  
|`Function`|省略可能、ただしか`Sub`または`Function`表示する必要があります。 代理人としてこのプロシージャを宣言`Function`値を返すプロシージャです。|  
|`name`|必須。 デリゲート型の名前標準変数の名前付け規則に従います。|  
|`typeparamlist`|任意。 このデリゲートの型パラメーターの一覧です。 複数の型パラメーターは、コンマで区切られます。 必要に応じて、型パラメーターごとに宣言できますバリアントを使用して`In`と`Out`ジェネリック修飾子です。 囲む必要があります、[型リスト](../../../visual-basic/language-reference/statements/type-list.md)かっこで囲まれたを導入し、`Of`キーワード。|  
|`parameterlist`|任意。 呼び出されると、プロシージャに渡されるパラメーターの一覧です。 囲む必要があります、[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)かっこ内に示します。|  
|`type`|指定するかどうかは必須、`Function`プロシージャです。 戻り値のデータ型。|  
  
## <a name="remarks"></a>コメント  
 `Delegate`ステートメントは、デリゲート クラスのパラメーターと戻り値の種類を定義します。 このデリゲート クラスのインスタンスを作成するパラメーターと戻り値の型が一致するプロシージャを使用できます。 プロシージャし、後で呼び出せるように、デリゲート インスタンスを使用して、デリゲートを呼び出すことによって`Invoke`メソッドです。  
  
 名前空間、モジュール、クラス、または構造のレベルでは、プロシージャ内ではなく、デリゲートを宣言できます。  
  
 各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。 デリゲート コンス トラクターに渡す引数は、メソッドへの参照、またはラムダ式である必要があります。  
  
 メソッドへの参照を指定するには、次の構文を使用します。  
  
 `AddressOf` [`expression`.]`methodname`  
  
 コンパイル時の `expression` の型は、シグネチャがデリゲート クラスのシグネチャと同じで、指定された名前のメソッドを持つクラスまたはインターフェイスである必要があります。 `methodname` は、共有メソッドまたはインスタンス メソッドのいずれかにできます。 クラスの既定メソッドに対してデリゲートを作成する場合も、`methodname` は省略できません。  
  
 ラムダ式を指定するには、次の構文を使用します。  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 関数のシグネチャは、デリゲート型のシグネチャと一致している必要があります。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 デリゲートの詳細については、次を参照してください。[デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)です。  
  
## <a name="example"></a>例  
 次の例では、 `Delegate` 2 つの数値で動作するいると、数を返すデリゲートを宣言するステートメント。 `DelegateTest`メソッドは、この型のデリゲートのインスタンスを使用し、番号のペアを操作するために使用します。  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
