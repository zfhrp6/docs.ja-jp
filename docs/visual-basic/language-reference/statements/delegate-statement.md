---
title: "Delegate ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
dev_langs:
- VB
helpviewer_keywords:
- delegate keyword
- Delegate statement
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
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
ms.openlocfilehash: 9ac9e28c82f8a6b5a9c1398961d831c956a649e0
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-statement"></a>Delegate ステートメント
デリゲートを宣言するために使用します。 デリゲートは、参照型を参照する、`Shared`メソッド、型またはオブジェクトのインスタンス メソッドにします。 パラメーターと戻り値の型が一致するプロシージャは、このデリゲート クラスのインスタンスを作成するために使用します。 プロシージャし、後で呼び出せるデリゲート インスタンスの作成。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attrlist`|省略可能です。 このデリゲートに適用される属性の一覧です。 複数の属性を指定するときは、コンマで区切ります。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこで ("`<`「と」`>`") です。|  
|`accessmodifier`|省略可能です。 デリゲートにアクセスできるコードを指定します。 次のいずれかの値を指定します。<br /><br /> -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)します。 デリゲートを宣言した要素にアクセスするすべてのコードにアクセスできます。<br />-   [保護されている](../../../visual-basic/language-reference/modifiers/protected.md)します。 唯一のコードは、デリゲートのクラスまたは派生クラスでは、それにアクセスできます。<br />-   [フレンド](../../../visual-basic/language-reference/modifiers/friend.md)します。 デリゲートが同じアセンブリ内のコードだけにアクセスできます。<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)します。 デリゲートを宣言する要素内のコードだけがアクセスできます。<br /><br /> 指定できます`Protected Friend`デリゲートのクラスや派生クラスでは、同じアセンブリ内のコードからのアクセスを有効にします。|  
|`Shadows`|省略可能です。 このデリゲートを宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされた要素のセットを非表示にすることを示します。 宣言された要素は、他の任意の種類の要素でシャドウできます。<br /><br /> シャドウされた要素は、その要素をシャドウする派生クラスからは使用できません。ただし、シャドウする要素がアクセスできない要素の場合は例外です。 たとえば場合、`Private`要素をシャドウする基本クラスの要素では、コードへのアクセス許可がない、`Private`要素は、基本クラスの要素を代わりにアクセスします。|  
|`Sub`|省略可能、ただし、いずれかの`Sub`または`Function`必要があります。 このプロシージャがデリゲートとしてを宣言`Sub`値を返さないプロシージャです。|  
|`Function`|省略可能、ただし、いずれかの`Sub`または`Function`必要があります。 このプロシージャがデリゲートとしてを宣言`Function`値を返すプロシージャです。|  
|`name`|必須です。 デリゲートの型の名前標準的な変数の名前付け規則に従います。|  
|`typeparamlist`|省略可能です。 このデリゲートの型パラメーターの一覧です。 複数の型パラメーターは、コンマで区切られます。 必要に応じて、それぞれの型パラメーター宣言できますバリアントを使用して`In`と`Out`汎用修飾子です。 囲む必要があります、[型リスト](../../../visual-basic/language-reference/statements/type-list.md)かっこで囲まれたを導入し、`Of`キーワードです。|  
|`parameterlist`|省略可能です。 呼び出されると、プロシージャに渡されるパラメーターの一覧。 囲む必要があります、[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)かっこ内に示します。|  
|`type`|指定するかどうかは必須、`Function`プロシージャです。 戻り値のデータ型。|  
  
## <a name="remarks"></a>コメント  
 `Delegate`ステートメントは、デリゲート クラスのパラメーターと戻り値の種類を定義します。 パラメーターと戻り値の型が一致するプロシージャは、このデリゲート クラスのインスタンスを作成するために使用します。 プロシージャし、後で呼び出せるように、デリゲート インスタンスを使用して、デリゲートを呼び出すことによって`Invoke`メソッドです。  
  
 プロシージャ内ではありませんが、名前空間、モジュール、クラスまたは構造のレベルでは、デリゲートを宣言できます。  
  
 各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。 デリゲート コンス トラクターに渡す引数は、メソッドまたはラムダ式への参照である必要があります。  
  
 メソッドへの参照を指定するには、次の構文を使用します。  
  
 `AddressOf` [`expression`.]`methodname`  
  
 コンパイル時の型、`expression`クラスまたはそのシグネチャがデリゲート クラスのシグネチャと一致する指定した名前のメソッドを格納しているインターフェイスの名前を指定する必要があります。 `methodname`共有メソッドまたはインスタンス メソッドのいずれかにすることができます。 `methodname`クラスの既定のメソッドのデリゲートを作成した場合でも、省略可能ではありません。  
  
 ラムダ式を指定するには、次の構文を使用します。  
  
 `Function`([`parm` As `type`, `parm2` As `type2`, ...])`expression`  
  
 デリゲート型の関数の署名が一致する必要があります。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 デリゲートの詳細については、次を参照してください。[デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)します。  
  
## <a name="example"></a>例  
 次の例では、`Delegate`の&2; つの数値で動作している数値を返すデリゲートを宣言するステートメントです。 `DelegateTest`メソッドは、この型のデリゲートのインスタンスを使用し、番号のペアで動作するように使用します。  
  
 [!code-vb[VbVbalrDelegates&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [ジェネリックの共変性と反変性](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [で](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [チェック アウトします。](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
