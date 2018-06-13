---
title: シャドウとオーバーライドの違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 94ce3e7fe25b7942730e6e89a53654b03d91c42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649634"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>シャドウとオーバーライドの違い (Visual Basic)
基底クラスから継承するクラスを定義するときする場合がありますを再定義する 1 つまたは複数の派生クラスで基底クラス要素。 シャドウとオーバーライドは、この目的では両方の使用可能なです。  
  
## <a name="comparison"></a>比較  
 シャドウとオーバーライドが使用されている場合、派生クラスは、基底クラスから継承し、1 つの宣言された要素と他の再定義します。 2 つの重要な違いがあります。  
  
 次の表では、シャドウとオーバーライドを比較します。  
  
||||  
|---|---|---|  
|比較のポイント|シャドウ|オーバーライドします。|  
|目的|派生クラスで既に定義されているメンバーを導入する後続の基本クラスの変更から保護します。|プロシージャまたはプロパティが同じ呼び出し元のシーケンスの別の実装を定義することによって、ポリモーフィズムを実現<sup>1</sup>|  
|再定義された要素|宣言されたいずれかの要素型|プロシージャのみ (`Function`、 `Sub`、または`Operator`) またはプロパティ|  
|再定義する要素|宣言されたいずれかの要素型|プロシージャまたは呼び出しシーケンスが同じプロパティのみ<sup>1</sup>|  
|再定義する要素のアクセス レベル|任意のアクセス レベル|上書きされた要素のアクセス レベルを変更することはできません。|  
|読みやすさと再定義する要素の書き込みの許可|任意の組み合わせ|読みやすさやすさのオーバーライドされたプロパティを変更することはできません。|  
|再定義の制御します。|基底クラス要素は、強制またはシャドウを禁止することはできません。|基底クラス要素を指定できます`MustOverride`、 `NotOverridable`、または `Overridable`|  
|キーワードの使用法|`Shadows` 派生クラスでは推奨`Shadows`どちらもと見なされます`Shadows`も`Overrides`指定<sup>2</sup>|`Overridable` または`MustOverride`基本クラスでは必須`Overrides`派生クラスで必要|  
|派生クラスから派生するクラスで再定義する要素の継承|継承された要素をシャドウ以降の派生クラスです。シャドウされた要素を非表示のまま<sup>3</sup>|継承された要素をオーバーライドするさらに派生クラスです。まだオーバーライド上書きされた要素|  
  
 <sup>1</sup> 、*コーリング シーケンス*要素型で構成されます (`Function`、 `Sub`、 `Operator`、または`Property`)、パラメーター リストの名前および戻り型。 プロパティ、またはその逆を持つプロシージャをオーバーライドすることはできません。 1 つの種類のプロシージャをオーバーライドすることはできません (`Function`、 `Sub`、または`Operator`) 別の種類を使用します。  
  
 <sup>2</sup>いずれかを指定しない場合`Shadows`または`Overrides`コンパイラが使用する再定義の種類を確認するために、警告メッセージを発行します。 警告を無視する場合は、シャドウ機構が使用されます。  
  
 <sup>3</sup>シャドウ シャドウする要素がさらに派生クラスでアクセス可能でない場合は継承されません。 シャドウ要素として宣言した場合など、 `Private`、派生クラスから派生したクラスがシャドウ要素ではなく元の要素を継承します。  
  
## <a name="guidelines"></a>ガイドライン  
 また、次の場合、オーバーライドする通常使用します。  
  
-   ポリモーフィックな派生クラスを定義します。  
  
-   安全のために、コンパイラが、同一の要素型と呼び出し元のシーケンスを適用します。  
  
 また、次の場合、シャドウ通常使用します。  
  
-   予想される、基本クラスが変更され、自分のものと同じ名前を使用して要素を定義します。  
  
-   要素の型の変更や呼び出しシーケンスの自由度ができます。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [方法: 自分で宣言した変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [方法: 派生クラスによって非表示になっている変数にアクセスする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
