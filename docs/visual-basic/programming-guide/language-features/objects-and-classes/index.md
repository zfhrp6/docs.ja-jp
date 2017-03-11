---
title: "Objects and Classes in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic]"
  - "objects [Visual Basic]"
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Objects and Classes in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*オブジェクト*とは、1 つの単位として扱うことのできるコードとデータの組み合わせです。  オブジェクトは、コントロールやフォームのようなアプリケーションの一部である場合もあります。  また、アプリケーション全体が 1 つのオブジェクトである場合もあります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でアプリケーションを作成する場合、作業では常にオブジェクトを使用します。  コントロール、フォーム、データ アクセス オブジェクトなど、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] に用意されたオブジェクトを使用できます。  また、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション内の、他のアプリエーションのオブジェクトも使用できます。  さらに、独自のオブジェクトを作成し、作成したオブジェクトにプロパティやメソッドを追加することも可能です。  オブジェクトは、プログラムの既成部品として機能します。オブジェクトを使うと、一度記述したコードを繰り返し再利用できます。  
  
 このトピックでは、オブジェクトの詳細について説明します。  
  
## クラスとオブジェクト  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の各オブジェクトは、*クラス*によって定義されます。  クラスによって、オブジェクトの変数、プロパティ、プロシージャ、およびイベントが説明されます。  オブジェクトは、クラスのインスタンスです。クラスを定義すると、必要なだけオブジェクトを作成できます。  
  
 オブジェクトとクラスの関係は、クッキーとクッキーの抜き型にたとえることができます。  クッキーの抜き型はクラスです。  抜き型は、大きさや形など、それぞれのクッキーの特徴を定義します。  このクラスを基にオブジェクトを作成します。  このオブジェクトに相当するのがクッキーです。  
  
 メンバーにアクセスする前に、オブジェクトを作成する必要があります。  
  
#### クラスからオブジェクトを作成するには  
  
1.  オブジェクトの作成元のクラスを決定します。  
  
2.  [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を記述して、クラス インスタンスを代入する変数を作成します。  変数の型は、目的のクラスの型にする必要があります。  
  
    ```  
  
    Dim nextCustomer As customer   
    ```  
  
3.  [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) キーワードを追加して、変数をそのクラスの新しいインスタンスに初期化します。  
  
    ```  
    Dim nextCustomer As New customer  
    ```  
  
4.  これで、オブジェクト変数を介してそのクラスのメンバーにアクセスできます。  
  
    ```  
  
    nextCustomer.accountNumber = lastAccountNumber + 1  
    ```  
  
> [!NOTE]
>  可能な限り、変数は代入するクラスの型を使用して宣言してください。  これは、*事前バインディング*と呼ばれます。  コンパイル時にクラス型がわからない場合は、変数を [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) で宣言しておき、*遅延バインディング*を行うことで対応できます。  ただし、遅延バインディングではパフォーマンスが遅くなり、また、ランタイム オブジェクトのメンバーに対するアクセスが制限されます。  詳細については、「[Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)」を参照してください。  
  
### 複数のインスタンス  
 クラスから新しく作成されたオブジェクトは、互いに同一であることがよくあります。  ただし、個々のオブジェクトとして存在した後は、他のインスタンスと関係なく、変数およびプロパティを変更できます。  たとえば、フォームに 3 つのチェック ボックスを追加した場合、各チェック ボックスのオブジェクトは <xref:System.Windows.Forms.CheckBox> クラスのインスタンスです。  各 <xref:System.Windows.Forms.CheckBox> オブジェクトは、クラスで定義されている同じ特性や機能 \(プロパティ、変数、プロシージャ、およびイベント\) を共有します。  その一方で、各オブジェクトはそれぞれ固有の名前を持ち、個別に有効または無効にしたり、フォーム上の異なる場所に配置したりできます。  
  
## オブジェクト メンバー  
 オブジェクトは、アプリケーションの要素であり、クラスの*インスタンス*です。  フィールド、プロパティ、メソッド、およびイベントは、オブジェクトの構成要素であり、オブジェクトの*メンバー*を構成します。  
  
### メンバー アクセス  
 オブジェクト変数の名前、ピリオド \(`.`\)、およびメンバーの名前の順で指定して、オブジェクトのメンバーにアクセスします。  <xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.Text%2A> プロパティを設定する例を次に示します。  
  
```  
warningLabel.Text = "Data not saved"  
```  
  
#### メンバーを一覧表示する IntelliSense  
 \[メンバーの一覧\] オプションを起動すると、たとえば、メンバー アクセス演算子としてピリオド \(`.`\) を入力したときに、IntelliSense によってクラスのメンバーが一覧表示されます。  クラスのインスタンスとして宣言された変数の名前の後にピリオドを入力した場合、IntelliSense によってすべてのインスタンス メンバーが一覧表示されますが、共有メンバーは表示されません。  クラス名自体の後にピリオドを入力した場合、IntelliSense によってすべての共有メンバーが一覧表示されますが、インスタンス メンバーは表示されません。  詳細については、「[IntelliSense の使用方法](/visual-studio/ide/using-intellisense)」を参照してください。  
  
### フィールドとプロパティ  
 *プロパティ*と*フィールド*は、オブジェクトに格納されている情報を表します。  プロシージャでローカル変数を取得および設定する場合と同じ方法で、代入ステートメントを使用して値を取得および設定します。  <xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.Width%2A> プロパティを取得し、<xref:System.Windows.Forms.Control.ForeColor%2A> プロパティを設定する例を次に示します。  
  
```  
Dim warningWidth As Integer = warningLabel.Width  
warningLabel.ForeColor = System.Drawing.Color.Red  
```  
  
 フィールドも*メンバー変数*と呼ばれます。  
  
 次の場合はプロパティ プロシージャを使用します。  
  
-   値を設定または取得する時期と方法を制御する必要がある場合。  
  
-   プロパティに評価する必要のある明確な値のセットがある場合。  
  
-   値の設定により、`IsVisible` のプロパティなど、オブジェクトの状態が大きく変化する場合。  
  
-   プロパティの設定により、他の内部変数が変更されたり、他のプロパティの値が変更される場合。  
  
-   プロパティを設定または取得する前に、一連の手順を実行する必要がある場合。  
  
 次の場合はフィールドを使用します。  
  
-   自己検証型の値である場合。  たとえば、`True` や `False` 以外の値を `Boolean` 変数に代入すると、エラーが発生するか、データ変換が自動的に実行されます。  
  
-   データ型でサポートされる範囲にある値がすべて有効である場合。  `Single` 型または `Double` 型のプロパティの多くがこれに当てはまります。  
  
-   プロパティが `String` データ型であり、文字列のサイズや値に制限がない場合。  
  
-   詳細については、「[Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)」を参照してください。  
  
### メソッド  
 *メソッド*は、オブジェクトが実行できる処理です。  たとえば、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> は、コンボ ボックスに新しいエントリを追加する、<xref:System.Windows.Forms.ComboBox> オブジェクトのメソッドです。  
  
 <xref:System.Windows.Forms.Timer> オブジェクトの <xref:System.Windows.Forms.Timer.Start%2A> メソッドの例を次に示します。  
  
```  
Dim safetyTimer As New System.Windows.Forms.Timer  
safetyTimer.Start()  
```  
  
 メソッドとは、オブジェクトによって公開される*プロシージャ*です。  
  
 詳細については、「[Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)」を参照してください。  
  
### イベント  
 イベントとは、オブジェクトによって認識されるアクション \(マウス クリックやキー入力など\) であり、それに応答するためのコードを記述できます。  イベントは、ユーザーによる操作やプログラム コードの結果として発生する場合と、システムによって発生する場合があります。  イベントを通知するコードの場合はイベントを*発生*させると言い、それに応答するコードの場合は*処理する*と言います。  
  
 オブジェクトが発生させるカスタム イベントを独自に作成し、他のオブジェクトに処理させることもできます。  詳細については、「[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)」を参照してください。  
  
### インスタンス メンバーおよび共有メンバー  
 クラスからオブジェクトを作成するとき、結果はそのクラスのインスタンスになります。  [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) キーワードを使用して宣言されていないメンバーは、厳密な意味で特定のインスタンスに属している*インスタンス メンバー*です。  あるインスタンスのインスタンス メンバーは、同じクラスの他のインスタンスにある同じメンバーとは無関係です。  たとえば、インスタンス メンバー変数は異なるインスタンスで異なる値を持つことができます。  
  
 `Shared` キーワードを使用して宣言されたメンバーは、特定のインスタンスにではなく、クラス全体に属している*共有メンバー*です。  作成したクラスのインスタンスの数にかかわらず、またインスタンスを作成していない場合でも、共有メンバーは 1 つだけ存在します。  たとえば、共有メンバー変数は、クラスにアクセスできるすべてのコードが利用できる値を 1 つだけ持っています。  
  
#### 非共有メンバーへのアクセス  
  
###### オブジェクトの非共有メンバーにアクセスするには  
  
1.  オブジェクトがそのクラスから作成され、オブジェクト変数に割り当てられていることを確認してください。  
  
    ```  
    Dim secondForm As New System.Windows.Forms.Form  
    ```  
  
2.  メンバーにアクセスするためのステートメントで、オブジェクト変数名の後に*メンバー アクセス演算子* \(`.`\)、次にメンバー名を続けて記述します。  
  
    ```  
    secondForm.Show()  
    ```  
  
#### 共有メンバーへのアクセス  
  
###### オブジェクトの共有メンバーにアクセスするには  
  
-   クラス名の後に*メンバー アクセス演算子* \(`.`\)、次にメンバー名を続けて記述します。  常にクラス名を使用して、オブジェクトの `Shared` メンバーに直接アクセスする必要があります。  
  
    ```  
    MsgBox("This computer is called " & Environment.MachineName)  
    ```  
  
-   既にクラスからオブジェクトを作成してある場合、オブジェクト変数を使用して、`Shared` メンバーにアクセスすることもできます。  
  
### クラスとモジュールの違い  
 クラスとモジュールの主な違いは、クラスはオブジェクトとしてインスタンス化でき、標準モジュールはインスタンス化できないことです。  標準モジュールのデータには 1 つのコピーしか存在しません。したがって、プログラムのある部分で標準モジュールのパブリック変数を変更した後、プログラムの別の部分で同じ変数を読み取ると、変更後の値が取得されます。  一方、オブジェクト データは、オブジェクトのインスタンスごとに存在します。  また、標準モジュールとは異なり、クラスはインターフェイスを実装できます。  
  
> [!NOTE]
>  `Shared` 修飾子をクラス メンバーに適用すると、そのクラス メンバーは、クラスの特定のインスタンスではなくクラス自身に関連付けられます。  そのメンバーに対しては、モジュール メンバーにアクセスするのと同じ方法で、クラス名によって直接アクセスできます。  
  
 クラスとモジュールでは、メンバーに使用されるスコープも異なります。  クラス内で定義されたメンバーは、クラスの特定のインスタンス内がスコープとなり、そのオブジェクトの有効期間にだけ存在します。  クラスの外側からクラス メンバーにアクセスするには、*Object*.*Member* の形式の完全修飾名を使用する必要があります。  
  
 一方、モジュール内で宣言したメンバーは既定でパブリック アクセスとなり、そのモジュールにアクセスできる任意のコードからアクセスできます。  つまり、標準モジュールの変数は、プロジェクトのどこからでも参照でき、プログラムが実行されている間ずっと存在するため、事実上のグローバル変数です。  
  
## クラスとオブジェクトの再利用  
 オブジェクトを使うと、一度宣言した変数やプロシージャをいつでも必要なときに再利用できます。  たとえば、アプリケーションにスペル チェック機能を追加する場合は、スペル チェック機能に必要なすべての変数やサポート関数を定義することになります。  スペル チェック プログラムをクラスとして作成すると、コンパイル済みアセンブリへの参照を追加するだけで、このスペル チェック プログラムを他のアプリケーションで再利用できるようになります。  さらに、既に他の人によって開発されたスペル チェック クラスを使うと、その分の開発の手間を省くことができます。  
  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] には、利用可能なコンポーネントの例が数多くあります。  次の例では、<xref:System> 名前空間の <xref:System.TimeZone> クラスを使用しています。  <xref:System.TimeZone> には、現在のコンピューター システムのタイム ゾーンに関する情報を取得できるメンバーがあります。  
  
```  
Public Sub examineTimeZone()  
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone  
    Dim s As String = "Current time zone is "  
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "  
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "  
    s &= "different from UTC (coordinated universal time)"  
    s &= vbCrLf & "and is currently "  
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "  
    s &= "on ""summer time""."  
    MsgBox(s)  
End Sub  
```  
  
 この例では、最初の [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) で、<xref:System.TimeZone> 型のオブジェクト変数を宣言し、これを <xref:System.TimeZone.CurrentTimeZone%2A> プロパティで返される <xref:System.TimeZone> オブジェクトに割り当てています。  
  
## オブジェクト間の関係  
 オブジェクトを互いに関連付ける方法はいくつかあります。  主な関係として*階層*と*コンテインメント*があります。  
  
### 階層関係  
 より基本的なクラスから別のクラスが派生している場合、これらのクラスの間には*階層関係*があるといいます。  クラスの階層構造は、より一般的なクラスの内部処理形式である項目を記述する時に便利です。  
  
 次の例では、通常の <xref:System.Windows.Forms.Button> のように動作し、前景色と背景色とを反転させるメソッドを公開する、特殊な <xref:System.Windows.Forms.Button> を定義します。  
  
##### 既存のクラスの派生クラスを定義するには  
  
1.  [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) を使用して、必要なオブジェクトの作成元となるクラスを定義します。  
  
     `Public Class reversibleButton`  
  
     クラスの最後のコード行の後には、必ず `End Class` ステートメントを指定してください。  既定では、`Class` ステートメントを入力したときに、統合開発環境 \(IDE: Integrated Development Environment\) によって自動的に `End Class` が挿入されます。  
  
2.  `Class` ステートメントの直後に [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md) を指定します。  新しいクラスの派生元のクラスを指定します。  
  
     `Inherits System.Windows.Forms.Button`  
  
     新しいクラスには、基本クラスで定義されているすべてのメンバーが継承されます。  
  
3.  派生クラスで公開する追加のメンバー用のコードを追加します。  たとえば、`reverseColors` メソッドを追加する場合、派生クラスは次のようになります。  
  
    ```  
    Public Class reversibleButton  
        Inherits System.Windows.Forms.Button  
        Public Sub reverseColors()   
            Dim saveColor As System.Drawing.Color = Me.BackColor  
            Me.BackColor = Me.ForeColor  
            Me.ForeColor = saveColor  
        End Sub  
    End Class   
    ```  
  
     この `reversibleButton` クラスのオブジェクトを作成すると、作成したオブジェクトでは、<xref:System.Windows.Forms.Button> クラスのすべてのメンバーに加え、`reversibleButton` で定義した `reverseColors` メソッドなどの新しいメンバーにアクセスできます。  
  
 派生クラスは、派生元のクラスからメンバーを継承するため、クラスの階層構造のレベルが深くなるにつれてより複雑なクラスを作成できます。  詳細については、「[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
#### コードのコンパイル  
 コンパイラでは、新規クラスの派生元とするクラスにアクセスできる必要があります。  このためには、上の例で示したように名前を完全に修飾することや、[Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) で名前空間を指定することが必要になる場合があります。  クラスが別のプロジェクト内にある場合は、そのプロジェクトへの参照を追加することも必要になる場合があります。  詳細については、「[プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)」を参照してください。  
  
### コンテインメント関係  
 オブジェクト間の別の関係として、*コンテインメント関係*があります。  コンテナー オブジェクトとは、論理的に他のオブジェクトをカプセル化するオブジェクトです。  たとえば、<xref:System.OperatingSystem> オブジェクトは論理的に <xref:System.Version> オブジェクト \(<xref:System.OperatingSystem.Version%2A> プロパティによって返される\) を含んでいます。  コンテナー オブジェクトが物理的に他のオブジェクトを含んでいるわけではないことに注意してください。  
  
#### コレクション  
 オブジェクトの実際のコンテインメントを表すものの 1 つが*コレクション*です。  コレクションは、列挙できる、類似したオブジェクトのグループです。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) には、コレクションの項目を反復処理するための特別な構文があります。  さらに、コレクションでは、多くの場合、<xref:Microsoft.VisualBasic.Collection.Item%2A> を使って、インデックスや関連付けた一意の文字列で要素を取得できます。  コレクションは、インデックスを使わずに項目を追加したり削除したりできるため、配列よりも使い方が簡単です。  使い方が簡単なため、フォームやコントロールの格納によく使われます。  
  
## 関連トピック  
 [Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 クラスを作成する方法を操作手順に従って説明します。  
  
 [Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 オーバーロードされたプロパティとメソッド  
  
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 継承の修飾子、メソッドとプロパティのオーバーライド、MyClass、および MyBase について説明します。  
  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 クラス インスタンスの作成と破棄について説明します。  
  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 データ型のクラス定義を記述することなくオブジェクトを作成できる匿名型の作成方法および使用方法について説明します。  
  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 1 つの式で名前付きの型と匿名型のインスタンスを作成するために使用するオブジェクト初期化子について説明します。  
  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 匿名型宣言内のプロパティ名と型を推論する方法について説明します。  推論の成功例と失敗例を示します。