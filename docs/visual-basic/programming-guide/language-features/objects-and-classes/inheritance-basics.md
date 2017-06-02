---
title: "継承の基本 (Visual Basic) |Microsoft ドキュメント"
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
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 58aee9f8c348eb06daec2b8c9e332f3f2775bcb6
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="inheritance-basics-visual-basic"></a>継承の基本 (Visual Basic)
`Inherits`という新しいクラスを宣言するステートメントが使用される、*クラスを派生*と呼ばれる、既存のクラスに基づいて、*基本クラス*します。 派生クラスでは、継承、およびプロパティ、メソッド、イベント、フィールド、および基本クラスで定義された定数は、拡張できます。 次のセクションが、継承の規則のいくつかを説明し、方法クラスを変更するのに使用できる修飾子を継承または継承されます。  
  
-   既定では、すべてクラスは継承とマークされていない限り、`NotInheritable`キーワードです。 クラスは、プロジェクト内の他のクラスまたはその他のプロジェクトで参照されるアセンブリのクラスから継承できます。  
  
-   複数の継承を許可する言語とは異なり[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のみ単一継承クラスでは、1 つの基本クラスを派生クラスでは、あることができます。 クラスに複数の継承は許可されていませんが、クラスは、複数のインターフェイスは、同じ結果を効果的に実現できますを実装できます。  
  
-   基底クラスでの制限付きの項目を公開することを防ぐためには、派生クラスのアクセスの種類がありますと等しいかそれより制限の厳しい、基本クラス。 たとえば、`Public`クラスは継承できません、`Friend`または`Private`クラス、および`Friend`クラスは継承できません、`Private`クラスです。  
  
## <a name="inheritance-modifiers"></a>継承の修飾子  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]次のクラス レベルのステートメントおよび継承をサポートする修飾子が導入されています。  
  
-   `Inherits`ステートメント: 基本クラスを指定します。  
  
-   `NotInheritable`修飾子、プログラマがクラスの基底クラスとして使用することを防止します。  
  
-   `MustInherit`修飾子: ことクラスは、基底クラスとしてのみ使用するものを指定します。 インスタンスを`MustInherit`クラスを直接作成することはできません。 派生クラスの基本クラスのインスタンス作成できるだけです。 (C++ や c# など他のプログラミング言語の用語が使用され*抽象クラス*をこのようなクラスを記述します)。  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>派生クラスのプロパティとメソッドをオーバーライドします。  
 既定では、派生クラスは基底クラスのプロパティとメソッドを継承します。 ある場合、継承されたプロパティまたはメソッドが派生クラスで動作を変えるがある*オーバーライド*します。 つまり、派生クラスでメソッドの新しい実装を定義することができます。 プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。  
  
-   `Overridable`-派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。  
  
-   `Overrides`— オーバーライド、`Overridable`プロパティまたはメソッドの基本クラスで定義します。  
  
-   `NotOverridable`-プロパティまたはメソッドの継承クラスでオーバーライドを禁止します。 既定では、`Public`メソッドは、`NotOverridable`です。  
  
-   `MustOverride`派生クラスでプロパティまたはメソッドをオーバーライドする必要があります。 ときに、`MustOverride`キーワードを使用すると、メソッドの定義から成るだけ`Sub`、 `Function`、または`Property`ステートメントです。 その他のステートメントは許可されませんし、具体的にはない`End Sub`または`End Function`ステートメントです。 `MustOverride`メソッドを宣言する必要があります`MustInherit`クラスです。  
  
 給与支払いを処理するクラスを定義するとします。 ジェネリック型を定義することが`Payroll`を含むクラス、`RunPayroll`典型的な&1; 週間の給与を計算する方法です。 使用して`Payroll`より特化されたの基本クラスとして`BonusPayroll`従業員のボーナスを配布するときに使用できるクラスです。  
  
 `BonusPayroll`クラスが継承、および、上書き、`PayEmployee`ベースで定義されているメソッド`Payroll`クラスです。  
  
 次の例は、基本クラスを定義`Payroll,`と派生クラスでは、 `BonusPayroll`、継承されたメソッドをオーバーライド`PayEmployee`します。 プロシージャ、`RunPayroll`を作成し、渡します、`Payroll`オブジェクトと`BonusPayroll`関数の場合、オブジェクト`Pay`を実行する、`PayEmployee`両方のオブジェクトのメソッドです。  
  
 [!code-vb[VbVbalrOOP #&28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase キーワード  
 `MyBase`キーワードはクラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。 `MyBase`オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーにアクセスする頻繁に使用します。 具体的には、`MyBase.New`を派生クラスのコンス トラクターから基本クラス コンス トラクターを明示的に呼び出すために使用します。  
  
 たとえば、基本クラスから継承されたメソッドをオーバーライドする派生クラスをデザインするとします。 オーバーライドされたメソッドは、基本クラスのメソッドを呼び出すおよび次のコード フラグメントで示すように、戻り値を変更できます。  
  
 [!code-vb[VbVbalrOOP #&109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 次のリストの使用に関する制限を説明する`MyBase`:  
  
-   `MyBase`直接の基本クラスとその継承されたメンバーを参照します。 使用することはできませんにアクセスする`Private`クラスのメンバーです。  
  
-   `MyBase`実際のオブジェクトではなく、キーワードとなります。 `MyBase`変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
-   メソッドを`MyBase`が適用される直接の基本クラスで定義する必要はありません、間接的に継承された基本クラスで定義することがあります。 修飾された参照の順序で`MyBase`正しくコンパイルするため、いくつかの基本クラスが、呼び出しに使用されるパラメーターの型と名前に一致するメソッドを含める必要があります。  
  
-   使用することはできません`MyBase`を呼び出す`MustOverride`基本クラスのメソッドです。  
  
-   `MyBase`それ自体を修飾するために使用できません。 したがって、次のコードは有効ではありません。  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`モジュールでは使用できません。  
  
-   `MyBase`としてマークされている基本クラスのメンバーにアクセスするために使用できない`Friend`基本クラスが別のアセンブリ内にある場合。  
  
 別の例と詳細については、次を参照してください。[方法: 派生クラスによって非表示変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)します。  
  
## <a name="the-myclass-keyword"></a>MyClass キーワード  
 `MyClass`キーワードが最初に実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。 `MyClass`ようになります`Me`ですべてのメソッドおよびプロパティを呼び出すが、`MyClass`メソッドまたはプロパティが場合と同様に扱われる[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)します。 そのため、メソッドまたはプロパティは左右されない派生クラスでオーバーライドします。  
  
-   `MyClass`実際のオブジェクトではなく、キーワードとなります。 `MyClass`変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。  
  
-   `MyClass`外側のクラスとその継承されたメンバーを参照します。  
  
-   `MyClass`修飾子として使用できる`Shared`メンバーです。  
  
-   `MyClass`内で使用できません、`Shared`メソッドがインスタンス メソッドの内部クラスの共有メンバーにアクセスするのに使用できます。  
  
-   `MyClass`標準的なモジュールでは使用できません。  
  
-   `MyClass`基本クラスで定義されていると、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。 このような参照と同じ意味を持つ`MyBase.`*メソッド*します。  
  
 次の例を比較`Me`と`MyClass`です。  
  
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
  
 にもかかわらず`derivedClass`オーバーライド`testMethod`、`MyClass`キーワード`useMyClass`オーバーライド、およびコンパイラの解決の効果の基底クラスのバージョンへの呼び出しを無効`testMethod`します。  
  
## <a name="see-also"></a>関連項目  
 [Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

