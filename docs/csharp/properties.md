---
title: プロパティ
description: C# のプロパティについて説明します。C# のプロパティには、検証、計算値、遅延評価、プロパティ変更通知の機能があります。
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 05e51d527dc3c05301fc85d7717c751dc46bf9fa
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="properties"></a>プロパティ

C# のプロパティは、非常に優れた機能です。 開発者は C# で定義されている構文を使用して、設計の意図を正確に表すコードを記述できます。

プロパティは、アクセスされたときにはフィールドのように振る舞います。
ただし、フィールドとは異なり、プロパティの実装ではアクセサーを使用します。プロパティがアクセスされたときや値を割り当てられたときに実行されるステートメントをアクセサーで定義します。

## <a name="property-syntax"></a>プロパティの構文

プロパティの構文は、フィールドを自然に拡張したものです。 フィールドで格納場所を定義します。

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

プロパティの定義には、プロパティの値を取得する `get` アクセサーとプロパティに値を割り当てる `set` アクセサーの宣言が含まれます。

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

上記の構文は "*自動プロパティ*" の構文です。 コンパイラによって、プロパティをバックアップするフィールドの格納場所が生成されます。 また、`get` アクセサーと `set` アクセサーの本体もコンパイラによって実装されます。

場合によっては、その型の既定以外の値にプロパティを初期化する必要があります。  C# では、プロパティの右中かっこの後で値を設定することにより可能です。 `FirstName` プロパティの初期値は `null` より空の文字列の方がよい場合があります。 その場合は次に示すように指定します。

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

これは、このトピックで後述するように、読み取り専用プロパティに最も役立ちます。

格納場所は、下に示すように、開発者が定義することもできます。

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

プロパティの実装が 1 つの式の場合は、*式形式のメンバー*を get アクセス操作子または set アクセス操作子に使用できます。

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

このトピックでは、該当する箇所ではこの簡単な構文を使います。

上に示したプロパティの定義は、読み取り/書き込みプロパティです。 set アクセサーの `value` に注目してください。 `set` アクセサーには常に、`value` という名前のパラメーターが 1 つあります。 `get` アクセサーは、プロパティの型に変換可能な値を返す必要があります (この例では `string`)。
 
これが構文の基本です。 さまざまな設計手法をサポートするバリエーションが多数あります。 これらを詳しく確認しながら、各種シナリオに応じた構文の選択肢を見てみましょう。

## <a name="scenarios"></a>シナリオ

ここまでに示した例は、検証が行われない読み取り/書き込みプロパティという、プロパティ定義の中でも単純なものでした。 目的のコードを `get` アクセサーと `set` アクセサーで記述することで、さまざまなシナリオに対応できます。

### <a name="validation"></a>検証

`set` アクセサーにコードを記述すると、プロパティが表す値を常に有効な値にすることができます。 たとえば、`Person` クラスに設定されているルールの 1 つに、名前は無指定または空白文字にできないというものがあるとします。 これは次のように記述できます。

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

上記の例では、名前を無指定または空白文字にしてはいけないというルールが強制的に適用されます。 もし開発者が下のように指定すると、

```csharp
hero.FirstName = "";
```

この割り当てに対して `ArgumentException` がスローされます。 プロパティの set アクセサーの戻り値は void でなければならないため、例外をスローすることで set アクセサーにエラーを報告します。

これが検証のシンプルな例です。 この構文を拡張して、シナリオに必要なあらゆる要素に対応できます。 たとえば、各種プロパティ間の関係をチェックしたり、外部条件に対して検証したりできます。 C# で有効なステートメントは、すべてプロパティ アクセサーでも有効です。

### <a name="read-only"></a>読み取り専用

ここまでのプロパティ定義はすべて、パブリック アクセサーを持つ読み取り/書き込みプロパティでした。 これ以外にも、プロパティに有効なアクセシビリティがあります。
たとえば、読み取り専用プロパティを作成したり、set アクセサーと get アクセサーに異なるアクセシビリティを設定したりすることができます。 具体例として、`Person` クラスで、クラス内の他のメソッドからのみ `FirstName` プロパティの値を変更できるようにしたい場合は、 set アクセサーのアクセシビリティを `public` ではなく `private` に設定します。

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

これで、`FirstName` プロパティにはどのコードからもアクセスできる一方で、値の割り当ては `Person` クラス内の他のコードからしかできなくなります。

制限を設定するアクセス修飾子を set アクセサーと get アクセサーのどちらか 1 つに追加することもできます。 個々のアクセサーには、プロパティ定義のアクセス修飾子よりも制限が強いアクセス修飾子を設定する必要があります。 上記は、`FirstName` プロパティが `public` ですが set アクセサーが `private` であるため、有効です。 `public` なアクセサーを持つ `private` なプロパティを宣言することはできません。 プロパティの宣言では、`protected`、`internal`、`protected internal`、`private protected`、`private` を宣言することもできます。   

`get` アクセサーに制限の高い修飾子を設定することも有効です。 たとえば、`public` なプロパティで、`get` アクセサーを `private` に制限できます。 ただし、このようなシナリオは実際にはほとんどありません。

また、コンストラクターやプロパティの初期化子でのみ設定できるように、プロパティに対する変更を制限することもできます。 `Person` クラスを次のように変更することができます。

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

この機能は、読み取り専用プロパティとして公開されるコレクションを初期化する場合に最もよく使われます。

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>計算されたプロパティ

プロパティが返す値は、メンバー フィールドの値でなくてもかまいません。 計算された値を返すプロパティを作成できます。 姓と名を連結する計算をしてフルネームを返すように `Person` オブジェクトを拡張してみましょう。

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

上の例では、"[文字列補間](../csharp/language-reference/tokens/interpolated.md)" 機能を使用して、フルネームを表す書式設定された文字列を作成しています。

"*式形式のメンバー*" を使用することもできます。式形式のメンバーを使用すると、計算された `FullName` プロパティを簡潔な方法で作成できます。

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
"*式形式のメンバー*" では、式が 1 つだけ含まれたメソッドを定義する "*ラムダ式*" 構文を使用します。 ここでは、その式が Person オブジェクトのフルネームを返しています。

### <a name="lazy-evaluated-properties"></a>遅延評価されたプロパティ

計算されたプロパティの概念をストレージと組み合わせて、"*遅延評価されたプロパティ*" を作成できます。  たとえば、`FullName` プロパティを更新して、プロパティが最初にアクセスされたときに文字列が書式設定されるようにすることができます。

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

ただし、上記のコードにはバグが含まれています。 コードによって `FirstName` プロパティと `LastName` プロパティのいずれかの値が更新されると、以前に評価された `fullName` フィールドは無効になります。 `fullName` フィールドが再計算されるように、`FirstName` プロパティと `LastName` プロパティの `set` アクセサーを更新する必要があります。

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

上の最終版では、必要になった場合にのみ `FullName` プロパティが評価されます。
以前に計算されたものが有効であれば、それが使用されます。 状態が変化したことで、以前に計算されたバージョンが無効になると、再計算が行われます。 このクラスを使用するにあたって、開発者は実装の詳細を知っている必要はありません。 内部で変化があっても Person オブジェクトの使用には影響しません。 これが、プロパティを使用してオブジェクトのデータ メンバーを公開するする重要な利点です。
 
### <a name="inotifypropertychanged"></a>INotifyPropertyChanged

プロパティ アクセサーでコードを記述する必要があるシナリオとして、値が変更されたことをデータ バインディング クライアントに通知するための `INotifyPropertyChanged` インターフェイスのサポートというものもあります。 プロパティの値が変更されると、オブジェクトはその変更を示す `PropertyChanged` イベントを発生させます。 データ バインディング ライブラリは、その変更に基づいて表示要素を更新します。 下のコードは、この Person クラスの `FirstName` プロパティに `INotifyPropertyChanged` を実装する方法を示しています。

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

`?.` は "*null 条件演算子*" と呼ばれる演算子です。 演算子の右側を評価する前に、null 参照がないかをチェックします。 チェックの結果、`PropertyChanged` イベントに対するサブスクライバーがない場合は、イベントを発生させるコードは実行されません。 その場合、評価は行われず `NullReferenceException` がスローされます。 詳細については、[`events`](delegates-events.md) に関するページを参照してください。 上記の例では、新たに `nameof` という演算子を使用して、記号としてのプロパティ名を文字列に変換しています。
`nameof` を使用すると、プロパティ名にタイプミスが含まれるというエラーを減らすことができます。

これも、アクセサーでコードを記述することで目的のシナリオをサポートできるケースの一例です。

## <a name="summing-up"></a>まとめ

プロパティは、クラスまたはオブジェクトに含まれた一種のスマート フィールドです。 オブジェクトの外部からは、オブジェクト内にあるフィールドのように見えます。 一方、プロパティは、C# の機能をどれでも自由に使用して実装できます。
検証、各種アクセシビリティ、遅延評価など、目的のシナリオで必要となる要素はすべて提供できます。
