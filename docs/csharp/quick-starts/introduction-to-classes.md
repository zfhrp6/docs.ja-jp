---
title: "クイック スタート - クラスの概要 - c# ガイド"
description: "最初の c# プログラムを作成およびオブジェクト指向の概念の調査"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c2b267562f78b359d5ceaa696ff9a9bdcffa5821
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-classes"></a>クラスの概要

このレッスンをインストールするいると仮定[.NET Core SDK](http://dot.net/core)、および任意のエディターです。 いずれかがあるない場合[Visual Studio Code](https://code.visualstudio.com/)、または[Visual Studio](https://www.visualstudio.com/) Mac または Windows です。

## <a name="create-your-application"></a>アプリケーションを作成します。

という名前のディレクトリを作成して、ターミナル ウィンドウを使用して**クラス**です。 アプリケーションをビルドします。 そのディレクトリと型に変更`dotnet new console`コンソール ウィンドウにします。 このコマンドでは、アプリケーションを作成します。 開いている**Program.cs**です。 次のようになります。

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

このクイック スタートでしようとしている銀行口座を表す新しい型を作成します。 通常の開発者は、別のテキスト ファイルの各クラスを定義します。 これにより管理プログラムのサイズが増加します。  という名前の新しいファイルを作成する**BankAccount.cs**で、**クラス**ディレクトリ。 

このファイルには、deefinition にが含まれます、***銀行口座***です。 オブジェクトの Oriented プログラミングの形式で型を作成することでコードの編成***クラス***です。 これらのクラスには、特定のエンティティを表すコードが含まれています。 `BankAccount`クラスは、銀行口座を表します。 コードでは、メソッドとプロパティを特定の操作を実装します。 このクイック スタートでは、銀行口座は、この動作をサポートします。

1. 銀行口座を一意に識別する 10 桁の数字があります。
1. または、所有者の名前を格納する文字列があります。
1. 残高を取得できます。
1. これは、預金を受け取ります。
1. これは、引き出しを受け取ります。
1. 初期のバランスを正の値にする必要があります。
1. 引出と、負の値のバランスを取ることはできません。

## <a name="define-the-bank-account-type"></a>銀行口座の種類を定義します。

その動作を定義するクラスの基本を作成することで開始することができます。 これは、次のようになります。

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

前に、構築済みで見てをみましょう。  `namespace`宣言は、コードを論理的に編成する方法を提供します。 このクイック スタートは比較的小さく、1 つの名前空間にすべてのコードを配置します。 

`public class BankAccount`クラス、または型の定義を作成します。 内のすべての`{`と`}`クラスに依存している宣言がクラスの動作を定義します。 5 つ***メンバー***の`BankAccount`クラスです。 最初の 3 つが***プロパティ***です。 プロパティは、データ要素し、検証またはその他の規則を適用するコードを持つことができます。 最後の 2 つ***メソッド***です。 メソッドのコード ブロックは、1 つの関数を実行します。 各メンバーの名前の読み取りは必要があるのに十分な情報や、クラスの動作を理解する他の開発者に提供します。

## <a name="open-a-new-account"></a>新しいアカウントを開く

最初の機能を実装するのには、銀行口座を開きます。 顧客は、アカウントが開いたら、初期のバランスと、所有者、またはそのアカウントの所有者に関する情報が必要です。 

新しいオブジェクトを作成する、`BankAccount`型の意味を定義する、***コンス トラクター***それらの値を割り当てます。 A***コンス トラクター***クラスと同じ名前を持つメンバーであります。 そのクラス型のオブジェクトを初期化するために使用されます。 次のコンス トラクターを追加、`BankAccount`型。

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

使用して、オブジェクトを作成するときに、コンス トラクターが呼び出される[ `new`](../language-reference/keywords/new.md)です。 行を置き換えます。`Console.WriteLine("Hello World!");`で***program.cs***次の行 (交換`<name>`名)。

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance".);
```

型`dotnet run`に何が起こるかを確認します。  

アカウント番号が空であることに気付いたしますか。 問題は修正する時間を勧めします。 オブジェクトを作成するときは、アカウント番号を割り当てる必要があります。 それを作成する、呼び出し元の役割をすることはできません。 `BankAccount`クラス コードは、新しいアカウント番号を割り当てる方法を認識する必要があります。  これを行う簡単な方法では、10 桁の数字で開始します。 新しい各アカウントの作成時に、それをインクリメントします。 最後に、オブジェクトを作成するときは、現在のアカウントの数を格納します。

次のメンバー宣言を追加、`BankAccount`クラス。

```csharp
private static int accountNumberSeed = 1234567890;
```

これは、データ メンバーです。 `private`、つまりのみアクセスできる内のコードによって、`BankAccount`クラスです。 これは、プライベートな実装 (口座番号の生成方法です。) から (アカウント番号を持つ) などのパブリックの責任を分離する方法アカウント番号を割り当てるコンス トラクターに次の 2 行を追加します。

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

型`dotnet run`結果を確認します。

## <a name="create-deposits-and-withdrawals"></a>前払い金と引出を作成します。

銀行口座クラスは、前払い金と正常に動作する引き出しを許可する必要があります。 アカウントのすべてのトランザクションの履歴を作成することで前払い金と引出を実装してみましょう。 各トランザクションの残高を更新するだけのいくつか利点があります。 履歴は、すべてのトランザクションを監査および毎日残高の管理に使用できます。 必要なときにすべてのトランザクション履歴から残高を計算することによって修正される単一のトランザクションでエラーが正常に反映されます残高次の計算にします。

まず、トランザクションを表す新しい型を作成します。 これは、任意の責任を持たない単純型です。 いくつかのプロパティが必要です。 という名前の新しいファイルを作成する***Transaction.cs***です。 次のコードを追加します。

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

ここで、追加してみましょう。、<xref:System.Collections.Generic.List%601>の`Transaction`オブジェクトを、`BankAccount`クラスです。 次の宣言を追加します。

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601>クラスでは、別の名前空間をインポートする必要があります。 先頭に次のコードを追加**BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

ここで、変更してみましょう方法、`Balance`が報告されます。  これは、すべてのトランザクションの値を合計して確認できます。 宣言を変更`Balance`で、`BankAccount`には、次のクラス。

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

この例の重要な側面***プロパティ***です。 残高を計算しているは、値を別のプログラマが要求するときにようになりました。 計算処理は、すべてのトランザクションを列挙し、現在の残高として合計を提供します。

次に、実装、`MakeDeposit`と`MakeWithdrawal`メソッドです。 これらのメソッドは、最後の 2 つの規則が適用されます。 正の数、初期の分散である必要があると、任意の引き出しが負の値の分散を作成しないでください。 

これはの概念を導入***例外***です。 メソッドがその作業を正常に完了できないことを示す、標準的な方法は例外をスローすることです。 例外と関連付けられているメッセージの種類では、エラーについて説明します。 ここでは、`MakeDeposit`預金の量が負の場合、メソッドが例外をスローします。 `MakeWithdrawal`引き落とし金額が負の場合、または結果が負の値のバランスを取る引き出しを適用する場合、メソッドが例外をスローします。

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../language-reference/throw.md)ステートメント**スロー**例外。 現在のメソッドの実行が終了し、一致した場合に再開`catch`ブロックが見つかりました。 追加、`catch`このコードを少し後でテストするブロック。

残高を直接更新するのではなく、最初のトランザクションに追加できるように、コンス トラクターは 1 つの変更を取得する必要があります。 既に記述したので、`MakeDeposit`メソッド、コンス トラクターから呼び出します。 完成したコンス トラクターは、次のようになります。

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType>現在の日付と時刻を表すプロパティです。 いくつかの前払い金とで引出を追加することでこれをテストして`Main`メソッド。

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

次に、負の値の残高を含むアカウントを作成しようとしてエラー状態を検出することをテストします。

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

使用する、 [ `try`と`catch`ステートメント](../language-reference/keywords/try-catch.md)例外をスローする可能性があるコードのブロックをマークして想定するそれらのエラーをキャッチします。 負の値のバランスを取るのためをスローするコードをテストするのにと同じ手法を使用できます。

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

ファイルの保存と型`dotnet run`してみてください。

## <a name="challenge---log-all-transactions"></a>チャレンジ - すべてのトランザクション ログに記録

このクイック スタートを完了するを記述することができます、`GetAccountHistory`を作成するメソッド、`string`トランザクションの履歴。 このメソッドを追加、`BankAccount`型。

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

これは、使用、<xref:System.Text.StringBuilder>トランザクションごとに 1 つの行を含む文字列の書式を設定するクラス。 これらのクイック スタートで前述したコードの書式設定文字列を見てきました。 1 つの新しい文字が`\t`です。 出力を書式設定 タブを挿入するとします。

テストするには、この行を追加**Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

型`dotnet run`結果を確認します。

## <a name="next-steps"></a>次の手順

スタックしている場合は、このクイック スタートのソースを表示できます[当社の GitHub リポジトリに](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)

これですべてのクイック スタートが完了したです。 詳細についてはたい場合は、次のように再試行してください、[チュートリアル](../tutorials/index.md)