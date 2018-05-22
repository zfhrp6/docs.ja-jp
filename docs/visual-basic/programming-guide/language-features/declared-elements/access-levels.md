---
title: Visual Basic でのアクセス レベル
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 1e2d43f33a352d3f4502965c5368eb901e7bffdf
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic でのアクセス レベル
*アクセス レベル*宣言された要素の範囲にアクセスできるは、どのようなコードは、読み取りし、書き込みをするアクセス許可。 これは、アクセス レベルは、要素自体を宣言する方法だけでなく、要素のコンテナーのアクセス レベルによっても決定されます。 として宣言も含めに含まれる要素のいずれかのコンテナー要素にアクセスできないコードにアクセスできない、`Public`です。 たとえば、`Public`に変数が、`Private`構造体からではなく、構造体を含むクラスの内部からアクセスできるそのクラスの外です。  
  
## <a name="public"></a>Public  
 [パブリック](../../../../visual-basic/language-reference/modifiers/public.md)宣言ステートメントでキーワードは、要素を同じプロジェクト内のすべてのコード、プロジェクトを参照する他のプロジェクトおよびプロジェクトからビルドされたアセンブリからアクセスできることを指定します。 次のコードはサンプル`Public`宣言します。  
  
```vb  
Public Class classForEverybody  
```  
  
 使用することができます`Public`モジュール、インターフェイス、または名前空間レベルでのみです。 つまり、元のファイルまたは名前空間、またはインターフェイス、モジュール、クラスまたは構造体の内部ではなく、プロシージャ レベルでパブリック要素を宣言することができます。  
  
## <a name="protected"></a>プロテクト  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)宣言ステートメントでキーワードは、同じクラス内、またはこのクラスから派生したクラスから、要素をからのみアクセスできることを指定します。 次のコードはサンプル`Protected`宣言します。  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 使用することができます`Protected`クラスでのみレベル、およびだけ宣言する場合、クラスのメンバーです。 つまり、元のファイルまたは名前空間、またはインターフェイス、モジュール、構造体、またはプロシージャ内のレベルではなくが、クラスでは、保護されている要素を宣言することができます。  
  
## <a name="friend"></a>Friend  
 [フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)宣言ステートメントでキーワードは、同じアセンブリ内からではなく、要素をからアクセスできることを指定します、アセンブリ外です。 次のコードはサンプル`Friend`宣言します。  
  
```vb  
Friend stringForThisProject As String  
```  
  
 使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。 これは、元のファイルまたは名前空間、またはインターフェイス、モジュール、クラスまたは構造体の内部ではなく、プロシージャ レベルでフレンド要素を宣言することを意味します。  
  
## <a name="protected-friend"></a>保護されたフレンド  
 `Protected`と`Friend`宣言ステートメントでキーワードは、要素を派生クラスから、または内からアクセスできることを指定します。 同じアセンブリ、またはその両方です。 次のコードはサンプル`Protected Friend`宣言します。  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 使用することができます`Protected Friend`クラスでのみレベル、およびだけ宣言する場合、クラスのメンバーです。 つまり、元のファイルまたは名前空間、またはインターフェイス、モジュール、構造体、またはプロシージャ内のレベルではなくが、クラスでは、保護されたフレンド要素を宣言することができます。  
  
## <a name="private"></a>Private  
 [プライベート](../../../../visual-basic/language-reference/modifiers/private.md)宣言ステートメントでキーワードは、要素を同じモジュール、クラスまたは構造体からのみアクセスできることを指定します。 次のコードはサンプル`Private`宣言します。  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 `Private` は、モジュール レベルでのみ使用できます。 これは、プライベート要素は、モジュール、クラス、または構造体の内部ではなく、ソース ファイルまたは名前空間、インターフェイス内またはプロシージャ内のレベルを宣言することを意味します。  
  
 モジュール レベルで、`Dim`アクセス レベル キーワードを指定せず、ステートメントは等価、`Private`宣言します。 ただしを使用する場合、`Private`コードを読みやすくするためにキーワード。  

## <a name="private-protected"></a>保護されたプライベート

[プライベート保護](../../../language-reference/modifiers/private-protected.md)宣言ステートメントでキーワードは、外側のクラスと同じアセンブリに派生クラスからだけでなく、同じクラス内で、要素をからのみアクセスできることを指定します。 `Private Protected`以降では、Visual Basic 15.5 アクセス修飾子はサポートされています。

次の例は、`Private Protected`宣言します。

```vb
Private Protected internalValue As Integer
```

宣言することができます、`Private Protected`クラスの内部でだけの要素。 構造体、またはインターフェイス内で宣言することはできません。 またできますとして宣言するソース ファイルまたは名前空間、インターフェイスまたは構造体の内部またはプロシージャ内のレベル。

`Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。 これを使用するのには、Visual Basic プロジェクト (*.vbproj) ファイルに次の要素を追加します。 Visual Basic 15.5 として時間またはそれ以降は、システムにインストールされているが、最新バージョンの Visual Basic コンパイラでサポートされているすべての言語機能を利用することができます。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

使用する、`Private Protected`アクセス修飾子は、次の要素を Visual Basic プロジェクト (*.vbproj) ファイルを追加する必要があります。

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

 ## <a name="access-modifiers"></a>アクセス修飾子  
 アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 次の表では、アクセス修飾子を比較します。  
  
|アクセス修飾子|付与されるアクセス レベル|このアクセス レベルで宣言されていることができます要素|宣言コンテキスト内部では、この修飾子を使用することができます。|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|無制限の。<br /><br /> パブリック要素を参照するすべてのコードがアクセスできます。|インターフェイス<br /><br /> モジュール<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> クラス<br /><br /> 構造体|  
|`Protected`|継承。<br /><br /> 要素にアクセスできる保護対象の要素、または、そこから派生するクラスを宣言するクラス内のコードします。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|  
|`Friend`|アセンブリ:<br /><br /> フレンド要素にアクセスできる宣言されているアセンブリ内のコードします。|インターフェイス<br /><br /> モジュール<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|ソース ファイル<br /><br /> 名前空間<br /><br /> Interface<br /><br /> Module<br /><br /> クラス<br /><br /> 構造体|  
|`Protected` `Friend`|共用体の`Protected`と`Friend`:<br /><br /> 同じクラスまたは保護されたフレンド要素として、または要素のクラスから派生したクラス内では、同じアセンブリのコードは、アクセスできます。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|  
|`Private`|宣言コンテキスト。<br /><br /> 含まれる型は、内のコードを含め、プライベートの要素を宣言する型のコードは、要素にアクセスできます。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 構造体のメンバー<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|Module<br /><br /> クラス<br /><br /> 構造体|
|`Private Protected`|プライベートの保護されている要素を宣言するクラスにコードまたは bas クラスと同じアセンブリ内にある派生クラス内のコード。|インターフェイス<br /><br /> クラス<br /><br /> 構造体<br /><br /> 手順<br /><br /> プロパティ<br /><br /> メンバー変数<br /><br /> 定数<br /><br /> 列挙<br /><br /> イベント<br /><br /> 外部宣言<br /><br /> デリゲート|クラス|
  
## <a name="see-also"></a>関連項目  
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [方法: 変数の可用性を制御する](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
