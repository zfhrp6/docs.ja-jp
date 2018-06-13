---
title: '方法: オブジェクトのメンバーにアクセスする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 62be2955bd1f62fa5af4e54fb0af5e7dca29c421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650923"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>方法: オブジェクトのメンバーにアクセスする (Visual Basic)
オブジェクトを参照するオブジェクト変数がある場合は、多くの場合、メソッド、プロパティ、フィールド、イベントなど、そのオブジェクトのメンバーを操作します。 たとえば、作成すると、新しい<xref:System.Windows.Forms.Form>オブジェクトを設定することができます、<xref:System.Windows.Forms.Control.Text%2A>プロパティまたは呼び出しの<xref:System.Windows.Forms.Control.Focus%2A>メソッドです。  
  
## <a name="accessing-members"></a>メンバーへのアクセス  
 オブジェクトのメンバーは、それを参照して変数を使用してアクセスします。  
  
#### <a name="to-access-members-of-an-object"></a>オブジェクトのメンバーにアクセスするには  
  
-   メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     メンバーが場合[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)変数にアクセスする必要はありません。  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>既知の型のオブジェクトのメンバーへのアクセス  
 コンパイル時にオブジェクトの種類を把握している場合を使えば*事前バインディング*それを参照している変数のです。  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>コンパイル時に型を認識するオブジェクトのメンバーにアクセスするには  
  
1.  変数に代入するオブジェクトの型にするオブジェクト変数を宣言します。  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     `Option Strict On`、のみ割り当てることができます<xref:System.Windows.Forms.Form>オブジェクト (またはから派生した型のオブジェクトを<xref:System.Windows.Forms.Form>) に`extraForm`です。 クラスまたは拡大は、変換を含む構造体を定義するかどうか`CType`への変換<xref:System.Windows.Forms.Form>、することができますもそのクラスを割り当てるモデルまたは構造に`extraForm`です。  
  
2.  メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。  
  
    ```  
    extraForm.Show()  
    ```  
  
     メソッドとプロパティに固有のすべてにアクセスすることができます、<xref:System.Windows.Forms.Form>新機能に関係なく、クラス、`Option Strict`設定します。  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>不明な型のオブジェクトのメンバーへのアクセス  
 使用する必要があるコンパイル時に、オブジェクトの型がわからない場合*遅延バインディング*の任意の変数を参照しています。  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>対象のわからない型コンパイル時にオブジェクトのメンバーにアクセスするには  
  
1.  オブジェクト変数を宣言である、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)です。 (として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>)。  
  
    ```  
    Dim someControl As Object  
    ```  
  
     `Option Strict On`で定義されているメンバーのみにアクセスすることができます、<xref:System.Object>クラスです。  
  
2.  メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。  
  
    ```  
    someControl.GetType()  
    ```  
  
     オブジェクト変数に代入する任意のオブジェクトのメンバーにアクセスできるようにするには、設定する必要があります`Option Strict Off`です。 これを行うと、コンパイラが指定されたメンバーが変数に割り当てるオブジェクトによって公開されることを保証することはできません。 オブジェクトにアクセスしようとするメンバーを公開していない場合、<xref:System.MemberAccessException>例外が発生します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
