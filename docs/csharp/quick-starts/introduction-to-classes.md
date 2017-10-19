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
# <a name="introduction-to-classes"></a><span data-ttu-id="ce332-103">クラスの概要</span><span class="sxs-lookup"><span data-stu-id="ce332-103">Introduction to classes</span></span>

<span data-ttu-id="ce332-104">このレッスンをインストールするいると仮定[.NET Core SDK](http://dot.net/core)、および任意のエディターです。</span><span class="sxs-lookup"><span data-stu-id="ce332-104">This lesson assumes that you've installed [.NET Core SDK](http://dot.net/core), and an editor of your choice.</span></span> <span data-ttu-id="ce332-105">いずれかがあるない場合[Visual Studio Code](https://code.visualstudio.com/)、または[Visual Studio](https://www.visualstudio.com/) Mac または Windows です。</span><span class="sxs-lookup"><span data-stu-id="ce332-105">If you don't have one, try [Visual Studio Code](https://code.visualstudio.com/), or [Visual Studio](https://www.visualstudio.com/) on Mac or Windows.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="ce332-106">アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-106">Create your application</span></span>

<span data-ttu-id="ce332-107">という名前のディレクトリを作成して、ターミナル ウィンドウを使用して**クラス**です。</span><span class="sxs-lookup"><span data-stu-id="ce332-107">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="ce332-108">アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ce332-108">You'll build your application there.</span></span> <span data-ttu-id="ce332-109">そのディレクトリと型に変更`dotnet new console`コンソール ウィンドウにします。</span><span class="sxs-lookup"><span data-stu-id="ce332-109">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="ce332-110">このコマンドでは、アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-110">This command creates your application.</span></span> <span data-ttu-id="ce332-111">開いている**Program.cs**です。</span><span class="sxs-lookup"><span data-stu-id="ce332-111">Open **Program.cs**.</span></span> <span data-ttu-id="ce332-112">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ce332-112">It should look like this:</span></span>

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

<span data-ttu-id="ce332-113">このクイック スタートでしようとしている銀行口座を表す新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-113">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="ce332-114">通常の開発者は、別のテキスト ファイルの各クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ce332-114">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="ce332-115">これにより管理プログラムのサイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="ce332-115">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="ce332-116">という名前の新しいファイルを作成する**BankAccount.cs**で、**クラス**ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ce332-116">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="ce332-117">このファイルには、deefinition にが含まれます、***銀行口座***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-117">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="ce332-118">オブジェクトの Oriented プログラミングの形式で型を作成することでコードの編成***クラス***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-118">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="ce332-119">これらのクラスには、特定のエンティティを表すコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ce332-119">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="ce332-120">`BankAccount`クラスは、銀行口座を表します。</span><span class="sxs-lookup"><span data-stu-id="ce332-120">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="ce332-121">コードでは、メソッドとプロパティを特定の操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="ce332-121">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="ce332-122">このクイック スタートでは、銀行口座は、この動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ce332-122">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="ce332-123">銀行口座を一意に識別する 10 桁の数字があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-123">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="ce332-124">または、所有者の名前を格納する文字列があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-124">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="ce332-125">残高を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce332-125">The balance can be retrieved.</span></span>
1. <span data-ttu-id="ce332-126">これは、預金を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ce332-126">It accepts deposits.</span></span>
1. <span data-ttu-id="ce332-127">これは、引き出しを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ce332-127">It accepts withdrawals.</span></span>
1. <span data-ttu-id="ce332-128">初期のバランスを正の値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-128">The initial balance must be positive.</span></span>
1. <span data-ttu-id="ce332-129">引出と、負の値のバランスを取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce332-129">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="ce332-130">銀行口座の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce332-130">Define the bank account type</span></span>

<span data-ttu-id="ce332-131">その動作を定義するクラスの基本を作成することで開始することができます。</span><span class="sxs-lookup"><span data-stu-id="ce332-131">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="ce332-132">これは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ce332-132">It would look like this:</span></span>

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

<span data-ttu-id="ce332-133">前に、構築済みで見てをみましょう。</span><span class="sxs-lookup"><span data-stu-id="ce332-133">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="ce332-134">`namespace`宣言は、コードを論理的に編成する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ce332-134">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="ce332-135">このクイック スタートは比較的小さく、1 つの名前空間にすべてのコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="ce332-135">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="ce332-136">`public class BankAccount`クラス、または型の定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-136">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="ce332-137">内のすべての`{`と`}`クラスに依存している宣言がクラスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce332-137">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="ce332-138">5 つ***メンバー***の`BankAccount`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ce332-138">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="ce332-139">最初の 3 つが***プロパティ***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-139">The first three are ***properties***.</span></span> <span data-ttu-id="ce332-140">プロパティは、データ要素し、検証またはその他の規則を適用するコードを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="ce332-140">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="ce332-141">最後の 2 つ***メソッド***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-141">The last two are ***methods***.</span></span> <span data-ttu-id="ce332-142">メソッドのコード ブロックは、1 つの関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="ce332-142">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="ce332-143">各メンバーの名前の読み取りは必要があるのに十分な情報や、クラスの動作を理解する他の開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="ce332-143">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="ce332-144">新しいアカウントを開く</span><span class="sxs-lookup"><span data-stu-id="ce332-144">Open a new account</span></span>

<span data-ttu-id="ce332-145">最初の機能を実装するのには、銀行口座を開きます。</span><span class="sxs-lookup"><span data-stu-id="ce332-145">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="ce332-146">顧客は、アカウントが開いたら、初期のバランスと、所有者、またはそのアカウントの所有者に関する情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="ce332-146">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="ce332-147">新しいオブジェクトを作成する、`BankAccount`型の意味を定義する、***コンス トラクター***それらの値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ce332-147">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="ce332-148">A***コンス トラクター***クラスと同じ名前を持つメンバーであります。</span><span class="sxs-lookup"><span data-stu-id="ce332-148">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="ce332-149">そのクラス型のオブジェクトを初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce332-149">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="ce332-150">次のコンス トラクターを追加、`BankAccount`型。</span><span class="sxs-lookup"><span data-stu-id="ce332-150">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="ce332-151">使用して、オブジェクトを作成するときに、コンス トラクターが呼び出される[ `new`](../language-reference/keywords/new.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce332-151">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="ce332-152">行を置き換えます。`Console.WriteLine("Hello World!");`で***program.cs***次の行 (交換`<name>`名)。</span><span class="sxs-lookup"><span data-stu-id="ce332-152">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance".);
```

<span data-ttu-id="ce332-153">型`dotnet run`に何が起こるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ce332-153">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="ce332-154">アカウント番号が空であることに気付いたしますか。</span><span class="sxs-lookup"><span data-stu-id="ce332-154">Did you notice that the account number is blank?</span></span> <span data-ttu-id="ce332-155">問題は修正する時間を勧めします。</span><span class="sxs-lookup"><span data-stu-id="ce332-155">It's time to fix that.</span></span> <span data-ttu-id="ce332-156">オブジェクトを作成するときは、アカウント番号を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-156">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="ce332-157">それを作成する、呼び出し元の役割をすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce332-157">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="ce332-158">`BankAccount`クラス コードは、新しいアカウント番号を割り当てる方法を認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-158">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="ce332-159">これを行う簡単な方法では、10 桁の数字で開始します。</span><span class="sxs-lookup"><span data-stu-id="ce332-159">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="ce332-160">新しい各アカウントの作成時に、それをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="ce332-160">Increment it when each new account is created.</span></span> <span data-ttu-id="ce332-161">最後に、オブジェクトを作成するときは、現在のアカウントの数を格納します。</span><span class="sxs-lookup"><span data-stu-id="ce332-161">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="ce332-162">次のメンバー宣言を追加、`BankAccount`クラス。</span><span class="sxs-lookup"><span data-stu-id="ce332-162">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="ce332-163">これは、データ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="ce332-163">This is a data member.</span></span> <span data-ttu-id="ce332-164">`private`、つまりのみアクセスできる内のコードによって、`BankAccount`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ce332-164">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="ce332-165">これは、プライベートな実装 (口座番号の生成方法です。) から (アカウント番号を持つ) などのパブリックの責任を分離する方法アカウント番号を割り当てるコンス トラクターに次の 2 行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ce332-165">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="ce332-166">型`dotnet run`結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="ce332-166">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="ce332-167">前払い金と引出を作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-167">Create deposits and withdrawals</span></span>

<span data-ttu-id="ce332-168">銀行口座クラスは、前払い金と正常に動作する引き出しを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-168">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="ce332-169">アカウントのすべてのトランザクションの履歴を作成することで前払い金と引出を実装してみましょう。</span><span class="sxs-lookup"><span data-stu-id="ce332-169">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="ce332-170">各トランザクションの残高を更新するだけのいくつか利点があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-170">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="ce332-171">履歴は、すべてのトランザクションを監査および毎日残高の管理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce332-171">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="ce332-172">必要なときにすべてのトランザクション履歴から残高を計算することによって修正される単一のトランザクションでエラーが正常に反映されます残高次の計算にします。</span><span class="sxs-lookup"><span data-stu-id="ce332-172">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="ce332-173">まず、トランザクションを表す新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="ce332-173">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="ce332-174">これは、任意の責任を持たない単純型です。</span><span class="sxs-lookup"><span data-stu-id="ce332-174">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="ce332-175">いくつかのプロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="ce332-175">It needs a few properties.</span></span> <span data-ttu-id="ce332-176">という名前の新しいファイルを作成する***Transaction.cs***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-176">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="ce332-177">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ce332-177">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="ce332-178">ここで、追加してみましょう。、<xref:System.Collections.Generic.List%601>の`Transaction`オブジェクトを、`BankAccount`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ce332-178">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="ce332-179">次の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="ce332-179">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="ce332-180"><xref:System.Collections.Generic.List%601>クラスでは、別の名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-180">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="ce332-181">先頭に次のコードを追加**BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="ce332-181">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="ce332-182">ここで、変更してみましょう方法、`Balance`が報告されます。</span><span class="sxs-lookup"><span data-stu-id="ce332-182">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="ce332-183">これは、すべてのトランザクションの値を合計して確認できます。</span><span class="sxs-lookup"><span data-stu-id="ce332-183">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="ce332-184">宣言を変更`Balance`で、`BankAccount`には、次のクラス。</span><span class="sxs-lookup"><span data-stu-id="ce332-184">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="ce332-185">この例の重要な側面***プロパティ***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-185">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="ce332-186">残高を計算しているは、値を別のプログラマが要求するときにようになりました。</span><span class="sxs-lookup"><span data-stu-id="ce332-186">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="ce332-187">計算処理は、すべてのトランザクションを列挙し、現在の残高として合計を提供します。</span><span class="sxs-lookup"><span data-stu-id="ce332-187">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="ce332-188">次に、実装、`MakeDeposit`と`MakeWithdrawal`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ce332-188">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="ce332-189">これらのメソッドは、最後の 2 つの規則が適用されます。 正の数、初期の分散である必要があると、任意の引き出しが負の値の分散を作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="ce332-189">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="ce332-190">これはの概念を導入***例外***です。</span><span class="sxs-lookup"><span data-stu-id="ce332-190">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="ce332-191">メソッドがその作業を正常に完了できないことを示す、標準的な方法は例外をスローすることです。</span><span class="sxs-lookup"><span data-stu-id="ce332-191">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="ce332-192">例外と関連付けられているメッセージの種類では、エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ce332-192">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="ce332-193">ここでは、`MakeDeposit`預金の量が負の場合、メソッドが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ce332-193">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="ce332-194">`MakeWithdrawal`引き落とし金額が負の場合、または結果が負の値のバランスを取る引き出しを適用する場合、メソッドが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ce332-194">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="ce332-195">[ `throw` ](../language-reference/throw.md)ステートメント**スロー**例外。</span><span class="sxs-lookup"><span data-stu-id="ce332-195">The [`throw`](../language-reference/throw.md) statment **throws** an exception.</span></span> <span data-ttu-id="ce332-196">現在のメソッドの実行が終了し、一致した場合に再開`catch`ブロックが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="ce332-196">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="ce332-197">追加、`catch`このコードを少し後でテストするブロック。</span><span class="sxs-lookup"><span data-stu-id="ce332-197">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="ce332-198">残高を直接更新するのではなく、最初のトランザクションに追加できるように、コンス トラクターは 1 つの変更を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce332-198">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="ce332-199">既に記述したので、`MakeDeposit`メソッド、コンス トラクターから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ce332-199">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="ce332-200">完成したコンス トラクターは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ce332-200">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="ce332-201"><xref:System.DateTime.Now?displayProperty=nameWithType>現在の日付と時刻を表すプロパティです。</span><span class="sxs-lookup"><span data-stu-id="ce332-201"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="ce332-202">いくつかの前払い金とで引出を追加することでこれをテストして`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="ce332-202">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="ce332-203">次に、負の値の残高を含むアカウントを作成しようとしてエラー状態を検出することをテストします。</span><span class="sxs-lookup"><span data-stu-id="ce332-203">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="ce332-204">使用する、 [ `try`と`catch`ステートメント](../language-reference/keywords/try-catch.md)例外をスローする可能性があるコードのブロックをマークして想定するそれらのエラーをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="ce332-204">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="ce332-205">負の値のバランスを取るのためをスローするコードをテストするのにと同じ手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce332-205">You can use the same technique to test the code that throws for a negative balance:</span></span>

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

<span data-ttu-id="ce332-206">ファイルの保存と型`dotnet run`してみてください。</span><span class="sxs-lookup"><span data-stu-id="ce332-206">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="ce332-207">チャレンジ - すべてのトランザクション ログに記録</span><span class="sxs-lookup"><span data-stu-id="ce332-207">Challenge - log all transactions</span></span>

<span data-ttu-id="ce332-208">このクイック スタートを完了するを記述することができます、`GetAccountHistory`を作成するメソッド、`string`トランザクションの履歴。</span><span class="sxs-lookup"><span data-stu-id="ce332-208">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="ce332-209">このメソッドを追加、`BankAccount`型。</span><span class="sxs-lookup"><span data-stu-id="ce332-209">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="ce332-210">これは、使用、<xref:System.Text.StringBuilder>トランザクションごとに 1 つの行を含む文字列の書式を設定するクラス。</span><span class="sxs-lookup"><span data-stu-id="ce332-210">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="ce332-211">これらのクイック スタートで前述したコードの書式設定文字列を見てきました。</span><span class="sxs-lookup"><span data-stu-id="ce332-211">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="ce332-212">1 つの新しい文字が`\t`です。</span><span class="sxs-lookup"><span data-stu-id="ce332-212">One new character is `\t`.</span></span> <span data-ttu-id="ce332-213">出力を書式設定 タブを挿入するとします。</span><span class="sxs-lookup"><span data-stu-id="ce332-213">That inserts a tab to format the output.</span></span>

<span data-ttu-id="ce332-214">テストするには、この行を追加**Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="ce332-214">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="ce332-215">型`dotnet run`結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="ce332-215">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce332-216">次の手順</span><span class="sxs-lookup"><span data-stu-id="ce332-216">Next Steps</span></span>

<span data-ttu-id="ce332-217">スタックしている場合は、このクイック スタートのソースを表示できます[当社の GitHub リポジトリに](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="ce332-217">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="ce332-218">これですべてのクイック スタートが完了したです。</span><span class="sxs-lookup"><span data-stu-id="ce332-218">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="ce332-219">詳細についてはたい場合は、次のように再試行してください、[チュートリアル](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="ce332-219">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>