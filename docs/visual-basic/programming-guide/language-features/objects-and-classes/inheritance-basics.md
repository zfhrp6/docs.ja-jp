---
title: "Inheritance Basics (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "derived classes, inheritance"
  - "MyClass keyword, using"
  - "MyBase keyword, using"
  - "Inherits statement, inheritance"
  - "overriding, Overridable keyword"
  - "MustInherit keyword, using"
  - "Overrides keyword, using"
  - "inheritance"
  - "MustInherit classes"
  - "MustOverride keyword, using"
  - "classes [Visual Basic], derived"
  - "NotInheritable keyword, using"
  - "base classes, extending properties and methods"
  - "NotOverridable keyword, using"
  - "base classes, inheritance"
  - "abstract classes, inheritance"
  - "overriding, Overrides keyword"
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Inheritance Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`Inherits` ステートメントは、既存のクラス \(*基本クラス*\) に基づいて新しいクラス \(*派生クラス*\) を宣言するときに使用します。  派生クラスは、基本クラスで定義されているプロパティ、メソッド、イベント、フィールド、および定数を継承します。また、派生クラスでこれらのプロパティ、メソッド、イベント、フィールド、および定数を拡張することもできます。  ここでは、継承の規則の一部と、クラスの継承方法を変更するための修飾子について説明します。  
  
-   既定では、`NotInheritable` キーワードが指定されていない限り、すべてのクラスを継承できます。  継承するクラスは、プロジェクト内の他のクラスでも、プロジェクトが参照している他のアセンブリのクラスでもかまいません。  
  
-   多重継承をサポートしている言語もありますが、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] がサポートしているのは単一継承だけです。したがって、派生クラスの基本クラスは常に 1 つだけです。  クラスでは多重継承することはできませんが、複数のインターフェイスを実装することはできます。複数のインターフェイスを実装すると、多重継承と同様の結果が得られます。  
  
-   基本クラスで制限されている項目が公開されるのを防ぐため、派生クラスのアクセス レベルは、基本クラスと同等またはそれより制限の厳しいレベルにする必要があります。  たとえば、`Public` クラスは `Friend` クラスまたは `Private` クラスを継承できません。また、`Friend` クラスは `Private` クラスを継承できません。  
  
## 継承の修飾子  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、継承をサポートするために、次に示すクラス レベルのステートメントと修飾子が導入されています。  
  
-   `Inherits` ステートメント — 基本クラスを指定します。  
  
-   `NotInheritable` 修飾子 — クラスを基本クラスとして使用できないように指定します。  
  
-   `MustInherit` 修飾子 — クラスを基本クラスとしてだけ使用するように指定します。  `MustInherit` クラスのインスタンスは直接作成できません。派生クラスの基本クラス インスタンスとして作成する必要があります。  このようなクラスは、C\+\+ や C\# などの他のプログラミング言語での*抽象クラス*に相当します。  
  
## 派生クラスにおけるプロパティとメソッドのオーバーライド  
 既定では、派生クラスは基本クラスのプロパティとメソッドを継承します。  継承されたプロパティまたはメソッドが派生クラスの中で異なる動作をしなければならない場合、このプロパティまたはメソッドを*オーバーライド*できます。  つまり、派生クラスに、メソッドの新しい実装を定義できます。  プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。  
  
-   `Overridable` — 派生クラスにおけるプロパティやメソッドのオーバーライドを許可します。  
  
-   `Overrides` — 基本クラスで定義されている `Overridable` のプロパティやメソッドをオーバーライドします。  
  
-   `NotOverridable` — 継承するクラスでプロパティやメソッドのオーバーライドを禁止します。  既定では、`Public` メソッドは `NotOverridable` です。  
  
-   `MustOverride` — 派生クラスにおけるプロパティやメソッドのオーバーライドを必須にします。  `MustOverride` キーワードを使用する場合、メソッドの定義で使用できるステートメントは、`Sub`、`Function`、および `Property` の各ステートメントだけです。  その他のステートメントは使用できません。特に、`End Sub` ステートメントや `End Function` ステートメントも使用しません。  `MustOverride` メソッドは、`MustInherit` クラスで宣言する必要があります。  
  
 給与支払いを処理するクラスを定義するとします。  まず、通常の 1 週間分の給与を計算する `RunPayroll` メソッドを含む汎用の `Payroll` クラスを定義します。  次に、`Payroll` を基本クラスとして、より特化した `BonusPayroll` クラスを作成します。これはボーナスの支給時に使用します。  
  
 `BonusPayroll` クラスでは、基本の `Payroll` クラスで定義されている `PayEmployee` メソッドを継承し、オーバーライドできます。  
  
 次の例では、基本クラス `Payroll,` と派生クラス `BonusPayroll` を定義しています。この派生クラスは、継承したメソッド `PayEmployee` をオーバーライドします。  `RunPayroll` プロシージャは、`Payroll` オブジェクトと `BonusPayroll` オブジェクトを作成し、`Pay` 関数に渡します。この関数は、この 2 つのオブジェクトの `PayEmployee` メソッドを実行します。  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## MyBase キーワード  
 `MyBase` キーワードは、クラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。  `MyBase` は、派生クラスでオーバーライドまたはシャドウされている基本クラスのメンバーにアクセスする目的でよく使用されます。  特に、派生クラスのコンストラクターから基本クラスのコンストラクターを明示的に呼び出すために、`MyBase.New` がよく使用されます。  
  
 たとえば、基本クラスから継承したメソッドをオーバーライドする派生クラスをデザインするとします。  この場合は、次の例で示すように、オーバーライドしたメソッドで基本クラスのメソッドを呼び出し、戻り値を変更できます。  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 `MyBase` を使用するときには、次の制約があります。  
  
-   `MyBase` が参照するのは、直接の基本クラスとそこで継承されているメンバーです。  クラスの `Private` メンバーへのアクセスには使用できません。  
  
-   `MyBase` はキーワードであり、実際のオブジェクトではありません。  `MyBase` は変数に代入したり、プロシージャに渡したりできません。また、`Is` 比較で使用することもできません。  
  
-   `MyBase` で修飾するメソッドは、必ずしも直接の基本クラスで定義される必要はありません。間接的に継承されている基本クラスで定義することもできます。  `MyBase` で修飾した参照が正しくコンパイルされるためには、呼び出しで使用されているパラメーターの名前と型に対応するメソッドが、いずれかの基本クラスに含まれている必要があります。  
  
-   `MyBase` を使って基本クラスの `MustOverride` メソッドを呼び出すことはできません。  
  
-   `MyBase` をそれ自体で修飾することはできません。  したがって、次のコードは無効です。  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` をモジュールで使用することはできません。  
  
-   基本クラスが異なるアセンブリ内にある場合は、`Friend` と指定されている基本クラスのメンバーに `MyBase` を使ってアクセスすることはできません。  
  
 詳細および他の例については、「[How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)」を参照してください。  
  
## MyClass キーワード  
 `MyClass` キーワードは、クラスの現在のインスタンスを元の実装に従って参照するオブジェクト変数のように動作します。  `MyClass` は `Me` と似ていますが、`MyClass` から呼び出されるメソッドおよびプロパティは、[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md) であるかのように扱われます。  したがって、メソッドまたはプロパティは、派生クラスでのオーバーライドによる影響を受けません。  
  
-   `MyClass` はキーワードであり、実際のオブジェクトではありません。  `MyClass` は変数に代入したり、プロシージャに渡したりできません。また、`Is` 比較で使用することもできません。  
  
-   `MyClass` が参照するのは、外側のクラスとそこで継承されているメンバーです。  
  
-   `MyClass` は、`Shared` メンバーの修飾子として使用できます。  
  
-   `MyClass` は、`Shared` メソッドの内部では使用できませんが、クラスの共有メンバーにアクセスするためにインスタンス メソッドの中で使用できます。  
  
-   `MyClass` を標準モジュールで使用することはできません。  
  
-   基本クラスで定義されていて、クラスで実装が提供されていないメソッドを、`MyClass` で修飾することもできます。  このような参照は、`MyBase.`*Method* と同じ意味になります。  
  
 `Me` と `MyClass` を比較した例を次に示します。  
  
```  
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
  
 `derivedClass` は `testMethod` をオーバーライドしていますが、`useMyClass` の `MyClass` キーワードによってオーバーライドの影響は無効になり、`testMethod` の基本クラス バージョンに対する呼び出しが行われます。  
  
## 参照  
 [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)