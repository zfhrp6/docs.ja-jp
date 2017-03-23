---
title: "オブジェクト指向プログラミング (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5491b3bd5a25908194d02063f688a319509bb77
ms.lasthandoff: 03/13/2017

---
# <a name="object-oriented-programming-visual-basic"></a>オブジェクト指向プログラミング (Visual Basic)
Visual Basic では、カプセル化、継承、多態性などオブジェクト指向プログラミングに完全にサポートを提供します。  
  
 *カプセル化*関連するプロパティ、メソッド、およびその他のメンバーのグループが&1; つの単位またはオブジェクトとして扱われることを意味します。  
  
 *継承*既存のクラスに基づいて新しいクラスを作成する機能について説明します。  
  
 *ポリモーフィズム*同じ意味で使用できる複数のクラスが持てる場合でも、各クラスがさまざまな方法で同じプロパティまたはメソッドを実装することを意味します。  
  
 このセクションでは、次の概念について説明します。  
  
-   [クラスとオブジェクト](#Classes)  
  
    -   [クラス メンバー](#Members)  
  
         [プロパティとパブリック フィールド](#Properties)  
  
         [メソッド](#Methods)  
  
         [コンストラクター](#Constructors)  
  
         [デストラクター](#Destructors)  
  
         [イベント](#Events)  
  
         [入れ子になったクラス](#NestedClasses)  
  
    -   [アクセス修飾子とアクセス レベル](#AccessModifiers)  
  
    -   [クラスをインスタンス化します。](#InstantiatingClasses)  
  
    -   [共有クラスおよびメンバー](#Static)  
  
    -   [匿名型](#AnonymousTypes)  
  
-   [継承](#Inheritance)  
  
    -   [メンバーをオーバーライドします。](#Overriding)  
  
-   [インターフェイス](#Interfaces)  
  
-   [ジェネリック](#Generics)  
  
-   [デリゲート](#Delegates)  
  
##  <a name="Classes"></a>クラスとオブジェクト  
 条件*クラス*と*オブジェクト*ときどき使われる、交換が、実際には、クラスを表す、*型*オブジェクトは使用中に、オブジェクトの*インスタンス*クラスのです。 そのため、オブジェクトを作成する機能といいます*インスタンス化*します。 設計図との対比を使って説明すると、クラスは設計図であり、オブジェクトはその設計図を基にした建築物です。  
  
 クラスを定義するコード例を次に示します。  
  
```vb  
Class SampleClass  
End Class  
```  
  
 Visual Basic は、軽量のバージョンのと呼ばれるクラスも用意されています。*構造*をは、オブジェクトの大きな配列を作成し操作する必要がある場合に役立ちますが大量のメモリを使用しません。  
  
 構造体を定義するコード例を次に示します。  
  
```vb  
Structure SampleStructure  
End Structure  
```  
  
 詳細については次を参照してください:  
  
-   [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
###  <a name="Members"></a>クラス メンバー  
 各クラスが異なることができますが*クラス メンバー*クラスのデータや、クラスの動作を定義するメソッドをさまざまなクラスとオブジェクト間の通信を提供するイベントを記述するプロパティが含まれています。  
  
####  <a name="Properties"></a>プロパティとパブリック フィールド  
 フィールドとプロパティは、オブジェクトに格納されている情報を表します。 フィールドは、直接読み取ったり設定したりできるので変数と似ています。  
  
 フィールドを定義するコード例を次に示します。  
  
```vb  
Class SampleClass  
    Public SampleField As String  
End Class  
```  
  
 プロパティには get プロシージャと set プロシージャがあり、これらを使用することで値の設定方法や戻り値をより細かく制御できます。  
  
 Visual Basic ではプロパティの値を格納するためのプライベート フィールドを作成するかバック グラウンドで自動的には、このフィールドを作成し、プロパティ プロシージャの基本的なロジックを提供と呼ばれる自動実装プロパティを使用することができます。  
  
 自動実装プロパティを定義するコード例を次に示します。  
  
```vb  
Class SampleClass  
    Public Property SampleProperty as String  
End Class  
```  
  
 プロパティ値の読み取りと書き込みのために追加の操作を実行する必要がある場合は、プロパティ値を格納するフィールドを定義し、値を格納および取得する基本的なロジックを実装します。  
  
```vb  
Class SampleClass  
    Private m_Sample As String  
    Public Property Sample() As String  
        Get  
            ' Return the value stored in the field.  
            Return m_Sample  
        End Get  
        Set(ByVal Value As String)  
            ' Store the value in the field.  
            m_Sample = Value  
        End Set  
    End Property  
End Class  
```  
  
 ほとんどのプロパティには、プロパティ値の設定と取得を行うための両方のメソッドまたはプロシージャがあります。 ただし、読み取り専用または書き込み専用のプロパティを作成して、プロパティの変更や読み取りを制限することもできます。 そのためには、Visual Basic では `ReadOnly` キーワードと `WriteOnly` キーワードを使用します。 ただし、自動実装プロパティは、読み取り専用または書き込み専用にすることはできません。  
  
 詳細については次を参照してください:  
  
-   [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
####  <a name="Methods"></a>メソッド  
 A*メソッド*オブジェクトが実行できる操作します。  
  
> [!NOTE]
>  Visual Basic には、メソッドを作成する方法が&2; つあります。メソッドが値を返さない場合は `Sub` ステートメントを使用し、メソッドが値を返す場合は `Function` ステートメントを使用します。  
  
 クラスのメソッドを定義するコード例を次に示します。  
  
```vb  
Class SampleClass  
    Public Function SampleFunc(ByVal SampleParam As String)  
        ' Add code here  
    End Function  
End Class  
```  
  
 クラスは、いくつかの実装を持つことができますか*オーバー ロード*のパラメーターまたはパラメーターの型の数が異なるものと同じ方法です。  
  
 メソッドをオーバーロードするコード例を次に示します。  
  
```vb  
Overloads Sub Display(ByVal theChar As Char)  
    ' Add code that displays Char data.  
End Sub  
Overloads Sub Display(ByVal theInteger As Integer)  
    ' Add code that displays Integer data.  
End Sub  
```  
  
 ほとんどの場合、メソッドはクラス定義内で宣言します。 ただし、Visual Basic もサポートしています*拡張メソッド*既存のクラス、クラスの実際の定義の外部にメソッドを追加するためのです。  
  
 詳細については次を参照してください:  
  
-   [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
-   [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
  
####  <a name="Constructors"></a>コンス トラクター  
 コンストラクターは、特定の型のオブジェクトを作成するときに自動的に実行されるクラス メソッドです。 コンストラクターは、通常、新しいオブジェクトのデータ メンバーを初期化します。 コンストラクターは、クラスの作成時に&1; 回だけ実行できます。 また、コンストラクター内のコードは常に、クラス内の他のすべてのコードより先に実行されます。 他のメソッドと同じように、コンストラクターにも複数のオーバーロードを作成できます。  
  
 クラスのコンストラクターを定義するコード例を次に示します。  
  
```vb  
Class SampleClass  
    Sub New(ByVal s As String)  
        // Add code here.  
    End Sub  
End Class  
```  
  
 詳細についてを参照してください:[オブジェクトの有効期間: オブジェクトが作成と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。  
  
####  <a name="Destructors"></a>デストラクター  
 デストラクターは、クラスのインスタンスを消滅させるために使用します。 .NET Framework では、アプリケーション内のマネージ オブジェクトのメモリの割り当てと解放は、ガベージ コレクターによって自動的に管理されます。 ただし、アプリケーションで作成されるアンマネージ リソースを適切にクリーンアップするために、デストラクターも必要になることがあります。 1 つのクラスに定義できるデストラクターは&1; つだけです。  
  
 デストラクターおよび .NET Framework のガベージ コレクションの詳細については、次を参照してください。[ガベージ コレクション](../../../standard/garbagecollection/index.md)します。  
  
####  <a name="Events"></a>イベント  
 クラスやオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。 イベントを送信する (またはを発生させます) クラスと呼ばれる、*パブリッシャー*し、受信する (処理) イベント クラスと呼ばれます*サブスクライバー*します。 イベントに関する詳細については、どのように発生し、処理を参照してください[イベント](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)です。  
  
-   イベントを宣言するには、使用、 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
-   イベントを発生させるを使用して、 [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)します。  
  
-   宣言型の方法を使用してイベント ハンドラーを指定するには、使用、 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)ステートメントおよび[処理](../../../visual-basic/language-reference/statements/handles-clause.md)句。  
  
-   動的に追加、削除、およびイベントに関連付けられているイベント ハンドラーを変更するを使用して、 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)と[RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)と共に、 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)します。  
  
####  <a name="NestedClasses"></a>入れ子になったクラス  
 別のクラス内で定義されたクラスと呼びます*入れ子になった*します。 既定では、入れ子になったクラスはプライベートです。  
  
```vb  
Class Container  
    Class Nested  
    ' Add code here.  
    End Class  
End Class  
```  
  
 入れ子になったクラスのインスタンスを作成するには、コンテナー クラスの名前に続けて、ドットと入れ子になったクラスの名前を指定します。  
  
```vb  
Dim nestedInstance As Container.Nested = New Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a>アクセス修飾子とアクセス レベル  
 すべてのクラスおよびクラス メンバーを使用して、その他のクラスに提供するアクセス レベルを指定できます*アクセス修飾子*します。  
  
 次のアクセス修飾子を使用できます。  
  
|Visual Basic の修飾子|定義|  
|---------------------------|----------------|  
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。|  
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|この型またはメンバーには、同じクラスのコードのみがアクセスできます。|  
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|この型またはメンバーには、同じクラスまたは派生クラスのコードのみがアクセスできます。|  
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。|  
|`Protected Friend`|この型またはメンバーには、同じアセンブリ内の任意のコード、または別のアセンブリ内の任意の派生クラスからアクセスできます。|  
  
 詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
###  <a name="InstantiatingClasses"></a>クラスをインスタンス化します。  
 オブジェクトを作成するには、クラスをインスタンス化する (クラスのインスタンスを作成する) 必要があります。  
  
```vb  
Dim sampleObject as New SampleClass()  
```  
  
 クラスをインスタンス化した後は、インスタンスのプロパティやフィールドに値を割り当てたり、クラスのメソッドを呼び出したりできます。  
  
```vb  
' Set a property value.  
sampleObject.SampleProperty = "Sample String"  
' Call a method.  
sampleObject.SampleMethod()  
```  
  
 クラスのインスタンス化のプロセスでプロパティに値を割り当てるには、オブジェクト初期化子を使用します。  
  
```vb  
Dim sampleObject = New SampleClass With   
    {.FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 詳細については次を参照してください:  
  
-   [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [オブジェクト初期化子 : 名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
  
###  <a name="Static"></a>共有クラスおよびメンバー  
 クラスの共有メンバーは、プロパティ、プロシージャ、またはクラスのすべてのインスタンスによって共有されているフィールドです。  
  
 共有メンバーを定義します。  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 共有メンバーにアクセスするには、このクラスのオブジェクトを作成せず、クラスの名前を使用します。  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Visual Basic での共有のモジュールは、メンバーのみを共有しており、インスタンス化することはできません。 非共有のプロパティ、フィールド、またはメソッドに、共有メンバーもアクセスできません。  
  
 詳細については次を参照してください:  
  
-   [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
###  <a name="AnonymousTypes"></a>匿名型  
 匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。 クラスは、コンパイラによって生成されます。 このクラスには使用可能な名前がなく、オブジェクトの宣言時に指定したプロパティが格納されます。  
  
 匿名型のインスタンスを作成するコード例を次に示します。  
  
```vb  
' sampleObject is an instance of a simple anonymous type.  
Dim sampleObject =   
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 詳細についてを参照してください:[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
##  <a name="Inheritance"></a>継承  
 継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。 メンバーが継承するクラスが呼び出されます、*基本クラス*、メンバーを継承するクラスを呼び出すと、*クラスを派生*します。 ただし、Visual Basic のすべてのクラスを暗黙的に継承、 <xref:System.Object>.NET クラスの階層構造をサポートし、すべてのクラスに下位レベルのサービスを提供するクラス</xref:System.Object>。  
  
> [!NOTE]
>  Visual Basic では、多重継承をサポートしていません。 つまり、派生クラスの&1; つだけの基本クラスを指定できます。  
  
 基底クラスを継承するコード例を次に示します。  
  
```vb  
Class DerivedClass  
    Inherits BaseClass  
End Class  
```  
  
 既定では、すべてのクラスが継承可能になります。 ただし、クラスを基底クラスとして使用できないように指定したり、基底クラスとしてのみ使用できるクラスを作成したりできます。  
  
 クラスを基底クラスとして使用できないように指定する方法を次に示します。  
  
```vb  
NotInheritable Class SampleClass  
End Class  
```  
  
 クラスが基底クラスとしてのみ使用され、インスタンス化できないように指定する方法を次に示します。  
  
```vb  
MustInherit Class BaseClass  
End Class  
```  
  
 詳細については次を参照してください:  
  
-   [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)  
  
-   [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
  
-   [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
  
###  <a name="Overriding"></a>メンバーをオーバーライドします。  
 既定では、派生クラスは基底クラスのすべてのメンバーを継承します。 継承したメンバーの動作を変更する場合は、そのメンバーをオーバーライドする必要があります。 つまり、派生クラスに、メソッド、プロパティ、またはイベントの新しい実装を定義できます。  
  
 プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。  
  
|Visual Basic の修飾子|定義|  
|---------------------------|----------------|  
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|派生クラスでのクラス メンバーのオーバーライドを許可します。|  
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|基底クラスで定義されている仮想メンバー (オーバーライドできるメンバー) をオーバーライドします。|  
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|継承するクラスでのメンバーのオーバーライドを禁止します。|  
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|派生クラスでのクラス メンバーのオーバーライドを必須にします。|  
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|基底クラスから継承されたメンバーを隠ぺいします。|  
  
##  <a name="Interfaces"></a>インターフェイス  
 インターフェイスは、クラスと同様にプロパティ、メソッド、およびイベントのセットを定義します。 ただし、クラスとは異なり、インターフェイスは実装を提供しません。 インターフェイスはクラスによって実装され、クラスとは別のエンティティとして定義されます。 インターフェイスを実装するクラスは、そのインターフェイスのあらゆる機能を定義に従って厳密に実装する必要があります。この点で、インターフェイスはコントラクトを表しています。  
  
 インターフェイスを定義するコード例を次に示します。  
  
```vb  
Public Interface ISampleInterface  
    Sub DoSomething()  
End Interface  
```  
  
 クラスにインターフェイスを実装するコード例を次に示します。  
  
```vb  
Class SampleClass  
    Implements ISampleInterface  
    Sub DoSomething  
        ' Method implementation.  
    End Sub  
End Class  
```  
  
 詳細については次を参照してください:  
  
-   [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
  
-   [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)  
  
##  <a name="Generics"></a>ジェネリック  
 クラス、構造体、インターフェイスおよび .NET Framework のメソッドを含めることができます*パラメーター入力*格納または使用できるオブジェクトの種類を定義します。 ジェネリックの最も一般的な例として、コレクションがあります。コレクションには、その中に格納されるオブジェクトの型を指定できます。  
  
 ジェネリック クラスを定義するコード例を次に示します。  
  
```vb  
Class SampleGeneric(Of T)  
    Public Field As T  
End Class  
```  
  
 ジェネリック クラスのインスタンスを作成するコード例を次に示します。  
  
```vb  
Dim sampleObject As New SampleGeneric(Of String)  
sampleObject.Field = "Sample string"  
```  
  
 詳細については次を参照してください:  
  
-   [ジェネリック](https://msdn.microsoft.com/library/ms172192)  
  
-   [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
  
##  <a name="Delegates"></a>デリゲート  
 A*委任*メソッドのシグネチャを定義する型は、互換性のあるシグネチャを持つ任意のメソッドへの参照を提供することができます。 メソッドは、デリゲートを使用して起動する (呼び出す) ことができます。 デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。  
  
> [!NOTE]
>  イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。 イベント処理でデリゲートを使用する方法の詳細については、次を参照してください。[イベント](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)です。  
  
 デリゲートを作成するコード例を次に示します。  
  
```vb  
Delegate Sub SampleDelegate(ByVal str As String)  
```  
  
 デリゲートで指定されたシグネチャに一致するメソッドへの参照を作成するコード例を次に示します。  
  
```vb  
Class SampleClass  
    ' Method that matches the SampleDelegate signature.  
    Sub SampleSub(ByVal str As String)  
        ' Add code here.  
    End Sub  
    ' Method that instantiates the delegate.  
    Sub SampleDelegateSub()  
        Dim sd As SampleDelegate = AddressOf SampleSub  
        sd("Sample string")  
    End Sub  
End Class  
```  
  
 詳細については次を参照してください:  
  
-   [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
  
-   [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
-   [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)
