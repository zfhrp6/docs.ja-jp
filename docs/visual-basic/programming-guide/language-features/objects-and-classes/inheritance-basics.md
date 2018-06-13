---
title: 継承の基本 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 9225e5fd9fa35ae06414018a109f66515f99363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655190"
---
# <a name="inheritance-basics-visual-basic"></a>継承の基本 (Visual Basic)
`Inherits`という、新しいクラスを宣言するステートメントを使用、*クラスを派生*と呼ばれる、既存のクラスに基づいて、*基底クラス*です。 派生クラスでは、継承、プロパティ、メソッド、イベント、フィールド、および、基底クラスで定義されている定数は、拡張できます。 次のセクションでは、継承、に対するルールの一部について説明し、方法クラスを変更するのに使用できる修飾子を継承継承されます。  
  
-   既定では、すべてクラスは継承でマークされていない限り、`NotInheritable`キーワード。 クラスは、プロジェクト内の他のクラスとは、プロジェクトを参照するその他のアセンブリのクラスから継承できます。  
  
-   複数の継承を許可する言語の場合とは異なり Visual Basic により、単一継承のみです。つまり、派生クラスでは、1 つだけの基本クラスを持つことができます。 クラスに複数の継承は許可されていませんが、クラスは、同じ結果を達成できる効果的に複数のインターフェイスを実装できます。  
  
-   基底クラスで制限付きの項目を公開することを防ぐためには、派生クラスのアクセスの種類は同じかまたはその基本クラスよりも制限をする必要があります。 たとえば、`Public`クラスは継承できません、`Friend`または`Private`クラス、および`Friend`クラスは継承できません、`Private`クラスです。  
  
## <a name="inheritance-modifiers"></a>継承の修飾子  
 Visual Basic では、次のクラス レベルのステートメントおよび継承をサポートする修飾子が導入されています。  
  
-   `Inherits` ステートメント: 基底クラスを指定します。  
  
-   `NotInheritable` 修飾子: プログラマがクラスの基底クラスとして使用することを防止します。  
  
-   `MustInherit` 修飾子: クラスが基底クラスとしてのみ使用するものであるを指定します。 インスタンス`MustInherit`クラスを直接作成することはできません。 のみ作成する必要が派生クラスの基本クラスのインスタンス。 (など、C++ および C# の場合、他のプログラミング言語という用語を使用する*抽象クラス*をこのようなクラスを記述します)。  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>派生クラスのプロパティとメソッドをオーバーライドします。  
 既定では、派生クラスは、その基本クラスからプロパティとメソッドを継承します。 継承されたプロパティまたはメソッドが派生クラスで異なった動作を持つことができます*オーバーライド*です。 つまり、派生クラスでメソッドの新しい実装を定義できます。 プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。  
  
-   `Overridable` — 派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。  
  
-   `Overrides` -よりも優先、`Overridable`プロパティまたはメソッドの基本クラスで定義します。  
  
-   `NotOverridable` — プロパティまたはメソッドを継承クラスでオーバーライドされないようにします。 既定では、`Public`メソッドは`NotOverridable`します。  
  
-   `MustOverride` -派生クラスでプロパティまたはメソッドをオーバーライドする必要があります。 ときに、`MustOverride`キーワードを使用して、メソッド定義から成るだけ`Sub`、 `Function`、または`Property`ステートメントです。 その他のステートメントは許可されませんし、具体的にはない`End Sub`または`End Function`ステートメントです。 `MustOverride` メソッドを宣言する必要があります`MustInherit`クラスです。  
  
 給与支払いを処理するクラスを定義するとします。 ジェネリック型を定義することが`Payroll`クラスを含む、`RunPayroll`典型的な週の給与を計算する方法です。 使用して、`Payroll`より専門の基本クラスとして`BonusPayroll`クラスは、従業員のボーナスを配布するときに使用する可能性があります。  
  
 `BonusPayroll`クラスが継承、および、上書き、`PayEmployee`ベースで定義されたメソッド`Payroll`クラスです。  
  
 次の例は、基底クラスを定義`Payroll,`と派生クラスでは、 `BonusPayroll`、継承されたメソッドをオーバーライドする`PayEmployee`です。 プロシージャ、`RunPayroll`を作成し、渡します、`Payroll`オブジェクトおよび`BonusPayroll`関数の場合、オブジェクト`Pay`を実行する、`PayEmployee`両方のオブジェクトのメソッドです。  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase キーワード  
 `MyBase`キーワードはクラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。 `MyBase` オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーにアクセスするよく使用されます。 具体的には、`MyBase.New`を派生クラスのコンス トラクターから基本クラスのコンス トラクターを明示的に呼び出すために使用します。  
  
 たとえば、基本クラスから継承されたメソッドをオーバーライドする派生クラスをデザインするとします。 オーバーライドされたメソッドは、基本クラスでメソッドを呼び出しますおよび次のコード フラグメントで示すように、戻り値を変更できます。  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 次のリストを使用して制限を説明する`MyBase`:  
  
-   `MyBase` 直接の基本クラスとその継承されたメンバーを参照します。 使用することはできませんにアクセスする`Private`クラスのメンバーです。  
  
-   `MyBase` 実際のオブジェクトではなく、キーワードとなります。 `MyBase` 変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
-   メソッドを`MyBase`修飾直接の基本クラスで定義されている必要はありません、間接的に継承の基本クラスの代わりに定義することがあります。 修飾された参照の順序で`MyBase`基底クラスのいくつか正しくコンパイルするための呼び出しで表示されるパラメーターの型と名前に一致するメソッドを含める必要があります。  
  
-   使用することはできません`MyBase`を呼び出す`MustOverride`基本クラスのメソッドです。  
  
-   `MyBase` それ自体を修飾するためには使用できません。 したがって、次のコードは有効ではありません。  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` モジュールでは使用できません。  
  
-   `MyBase` としてマークされている基本クラスのメンバーのアクセスに使用することはできません`Friend`場合は、基本クラスは、別のアセンブリ。  
  
 別の例および詳細については、次を参照してください。[する方法: 派生クラスによって非表示変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)です。  
  
## <a name="the-myclass-keyword"></a>MyClass キーワード  
 `MyClass`キーワードが最初に実装されたクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass` 似た`Me`ですべてのメソッドとプロパティを呼び出すが、`MyClass`メソッドまたはプロパティが場合と同様に扱われます[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)です。 したがって、メソッドまたはプロパティは影響を受けません派生クラスでオーバーライドすることで。  
  
-   `MyClass` 実際のオブジェクトではなく、キーワードとなります。 `MyClass` 変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
-   `MyClass` 外側のクラスとその継承されたメンバーを参照します。  
  
-   `MyClass` 修飾子として使用できる`Shared`メンバー。  
  
-   `MyClass` 内部で使用できない、`Shared`メソッドがインスタンス メソッドの内部クラスの共有メンバーにアクセスするのに使用できます。  
  
-   `MyClass` 標準モジュールでは使用できません。  
  
-   `MyClass` 基本クラスで定義されていると、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。 このような参照と同じ意味を持つ`MyBase.`*メソッド*です。  
  
 次の例を比較して`Me`と`MyClass`です。  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 場合でも`derivedClass`オーバーライド`testMethod`、`MyClass`でキーワード`useMyClass`の基底クラスのバージョンへの呼び出しをオーバーライドして、コンパイラの解決の効果を null`testMethod`です。  
  
## <a name="see-also"></a>関連項目  
 [Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
