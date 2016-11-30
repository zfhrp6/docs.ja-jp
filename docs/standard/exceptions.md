---
title: ".NET での例外の処理とスロー"
description: ".NET で例外を使用する方法を理解する"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf116df6-0042-46bf-be13-b69864816210
translationtype: Human Translation
ms.sourcegitcommit: 9584699ad7e745ae3cb059b1bb8327301c9a3286
ms.openlocfilehash: 5271b63a47aa2fcc81cd9c8b1ffd22e618829412

---

# <a name="handling-and-throwing-exceptions-in-net"></a>.NET での例外の処理とスロー

アプリケーションは、実行中に発生するエラーを一貫した方法で処理できなければなりません。 .NET では、一貫した方法でアプリケーションにエラーを通知するためのモデルが用意されています。 .NET 操作では、例外をスローすることによって障害の発生を示します。

## <a name="exceptions"></a>例外

例外とは、プログラムを実行することによって発生するエラー状態または予期しない動作のことです。 例外がスローされる原因として、コードまたは呼び出したコード (たとえば共有ライブラリ) 内に障害がある、オペレーティング システム リソースを使用できない、予期しない状態 (たとえば検証できないコード) をランタイムが検出したなどがあります。 アプリケーションは、他の状態からではなく、これらの状態のうちのいくつかから回復できます。 ほとんどのアプリケーション例外から回復できますが、ほとんどのランタイム例外からは回復できません。

.NET では、例外は [System.Exception](xref:System.Exception) クラスから継承されるオブジェクトです。 例外は問題が発生したコード領域からスローされます。 例外は、アプリケーションが処理するかプログラムが終了するまで、スタックに渡されます。

## <a name="exceptions-vs-traditional-error-handling-methods"></a>例外と従来のエラー処理メソッド

言語のエラー処理モデルは従来、エラーを検出してそれに対応したハンドラーを見つける言語固有の方法か、オペレーティング システムが備えているエラー処理機構のいずれかを使用していました。 .NET が例外処理を実装する方法は、次の利点をもたらします。

- 例外のスローと処理は、.NET プログラミング言語では同じように機能します。

- 例外を処理するための特定の言語構文を必要とせず、各言語が独自の構文を定義できます。

- 例外は、プロセス間、さらにはコンピューターの境界を越えてスローできます。

- プログラムの信頼性を高めるための例外処理コードをアプリケーションに追加できます。

例外には、リターン コードなどの他のエラー通知メソッドに優る利点があります。 例外がスローされ、それを処理しないと、ランタイムによってアプリケーションが終了されるため、エラーが見過ごされることはありません。 無効な値は、エラーのリターン コードの確認に失敗したコードの結果として、システムを経由した伝達を続行しません。 

## <a name="exception-class-and-properties"></a>Exception クラスとプロパティ

@System.Exception クラスは、例外の継承元となる基底クラスです。 たとえば、@System.InvalidCastException クラスの階層は次のようになります。

```
Object
  Exception
    SystemException
       InvalidCastException
```

@System.Exception クラスには、簡単に例外を理解することに役立つ次のプロパティがあります。

| プロパティ名 | 説明 |
| ------------- | ----------- |
| @System.Exception.Data | キーと値のペアの任意のデータを保持する @System.Collections.IDictionary です。 |
| @System.Exception.HelpLink | 例外の原因に関する詳細情報を提供するヘルプ ファイルには、URL (または URN) を保持できます。 |
| @System.Exception.InnerException | このプロパティを使用すると、例外処理中に一連の例外を作成して保持することができます。 既にキャッチされた例外を含む新しい例外を作成するのにも使用できます。 @System.Exception.InnerException プロパティの 2 つ目の例外によって、元の例外をキャプチャできます。これにより、2 つ目の例外を処理するコードが追加の情報を調べることができます。 たとえば、形式が正しくない引数を受け取るメソッドがあるとします。  コードは、引数の読み取りを試みますが、例外がスローされます。 このメソッドは例外をキャッチし､@System.FormatException. をスローします。例外がスローされた原因を判断するための呼び出し元の機能を向上させるには、ヘルパー ルーチンによってスローされた例外をキャッチし、発生したエラーの内容を示す例外をスローするメソッドが望ましい場合があります。 内部例外の参照を元の例外に設定できる、新しいより意味のある例外を作成できます。 この意味のある例外は、呼び出し元にスローすることができます。 この機能により、最初にスローされた例外で終了する一連のリンクされた例外を作成することができます。 |
| @System.Exception.Message | 例外の原因に関する詳細を提供します。
| @System.Exception.Source | エラーの原因となるアプリケーションまたはオブジェクトの名前を取得または設定します。 |
| @System.Exception.StackTrace | エラーが発生した場所を判断するために使用できるスタック トレースが含まれています。 デバッグ情報が使用できる場合には、スタック トレースにソース ファイル名とプログラム行番号が記述されます。 |

@System.Exception から継承したクラスのほとんどは追加メンバーを実装したり追加機能を提供したりしません。単に @System.Exception. から継承するのみです。したがって、例外の最も重要な情報は例外クラス、例外の名前と例外に含まれる情報の階層で検出されます。

@System.Exception, から派生したオブジェクトだけをスローおよびキャッチすることをお勧めしますが、@System.Object クラスから派生したオブジェクトはすべて例外としてスローすることができます。 @System.Exception. から派生していないオブジェクトのスローとキャッチは、すべての言語ではサポートされていないことに注意してください。

## <a name="common-exceptions"></a>一般的な例外

次の表は、一般的な例外とそれらの原因の例をいくつか示しています。

| 例外の種類 | 基本型 | 説明 | 例 |
| -------------- | --------- | ----------- | ------- |
| @System.Exception | @System.Object | すべての例外の基底クラスです。 | なし (この例外の派生クラスを使用)。 |
| @System.IndexOutOfRangeException | @System.Exception | 配列のインデックスが誤っている場合にのみ、ランタイムによってスローされます。 | 次のように、配列に対して配列の有効範囲外のインデックスを付けた場合。`arr[arr.Length+1]` |
| @System.NullReferenceException | @System.Exception | null オブジェクトが参照された場合にのみ、ランタイムによってスローされます。 | `object o = null; o.ToString();` |
| @System.InvalidOperationException | @System.Exception | 無効な状態の場合にメソッドによってスローされます。 | 基になるコレクションからアイテムを削除した後での、`Enumerator.GetNext()` の呼び出しです。 |
| @System.ArgumentException | @System.Exception | すべての引数の例外の基底クラスです。 | なし (この例外の派生クラスを使用)。 |
| @System.ArgumentNullException | @System.Exception | null の引数を許可しないメソッドによってスローされます。 | `String s = null; "Calculate".IndexOf (s);` |
| @System.ArgumentOutOfRangeException | @System.Exception | 引数が特定の範囲内にあることを検査するメソッドによってスローされます。 | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Try ブロックと Catch ブロックを使用して例外をキャッチする方法

例外をスローする可能性のあるコードのセクションを `try` ブロックに配置し、例外を処理するコードを `catch` ブロックに配置します。 `catch` ブロックは、キーワード `catch` で始まり、その後に例外の種類と実行するアクションが続く一連のステートメントです。

次のコード例では、`try`/`catch` ブロックを使用して可能性のある例外をキャッチします。 `Main` メソッドには、`try` ブロックと、`data.txt` と呼ばれるデータ ファイルを開き、ファイルから文字列を書き込む @System.IO.StreamReader ステートメントが含まれます。 次の `try` ブロックは、`try` によって生成される任意の例外をキャッチする `catch` ブロックです。

C#
```
using System;
using System.IO;

public class ProcessFile
{
    public static void Main()
    {
        try
        {
            StreamReader sr = File.OpenText("data.txt");
            Console.WriteLine("The first line of this file is {0}", sr.ReadLine());
            sr.Dispose();
        }
        catch (Exception e)
        {
            Console.WriteLine("An error occurred: '{0}'", e);
        }
    }
}
```

共通言語ランタイムは、catch ブロックでキャッチされなかった例外をキャッチします。 ランタイムの構成方法に応じて、デバッグ ダイアログ ボックスが表示されるか、プログラムの実行が停止され、例外情報を含むダイアログ ボックスが表示されるか、または STDERR にエラーが出力されます。

> [!NOTE] 
> ほぼすべてのコード行で、特に @System.OutOfMemoryException. などのように共通言語ランタイム自体によってスローされるなどの例外が発生することがあります。ほとんどのアプリケーションではこれらの例外に対処する必要はありませんが、他のユーザーが使用するライブラリ書き込むとき、この可能性があることに注意してください。 Try ブロック内でコードを設定するタイミングに関しては、「[例外の推奨事項](#best-practices-for-exceptions)」を参照してください。
 
## <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>catch ブロックで特定の例外を使用する方法

上記のコード例は、任意の例外をキャッチする基本的な `catch` ステートメントを示しています。 ただし、一般的には、基本的な `catch` ステートメントを使用するよりも、特定の種類の例外をキャッチするプログラミング手法を勧めします。

例外が発生すると、スタックに渡され、各 catch ブロックが処理する機会を与えられます。 catch ステートメントの順序が重要です。 一般的な例外 catch ブロックまたはコンパイラがエラーを発行する前に、特定の例外を対象とした catch ブロックを配置します。 適切な catch ブロックは、例外の種類を catch ブロックで指定された例外の名前に一致させることで決まります。 特定の catch ブロックがない場合は、汎用 catch ブロック (ある場合) によってキャッチされます。

次のコード例では、`try`/`catch` ブロックを使用して @System.InvalidCastException. をキャッチします。このサンプルは単一プロパティ、従業員レベル (`Emlevel`) で `Employee` というクラスを作成します。 メソッド `PromoteEmployee` は、オブジェクトを受け取って、従業員レベルをインクリメントします。 @System.DateTime インスタンスが `PromoteEmployee` メソッドに渡されたとき、@System.InvalidCastException が発生します。

C#
```
using System;

public class Employee
{
    //Create employee level property.
    public int Emlevel
    {
        get
        {
            return(emlevel);
        }
        set
        {
            emlevel = value;
        }
    }

    private int emlevel = 0;
}

public class Ex13
{
    public static void PromoteEmployee(Object emp)
    {
        //Cast object to Employee.
        Employee e = (Employee) emp;
        // Increment employee level.
        e.Emlevel = e.Emlevel + 1;
    }

    public static void Main()
    {
        try
        {
            Object o = new Employee();
            DateTime newyears = new DateTime(2001, 1, 1);
            //Promote the new employee.
            PromoteEmployee(o);
            //Promote DateTime; results in InvalidCastException as newyears is not an employee instance.
            PromoteEmployee(newyears);
        }
        catch (InvalidCastException e)
        {
            Console.WriteLine("Error passing data to PromoteEmployee method. " + e.Message);
        }
    }
}
```

## <a name="how-to-use-finally-blocks"></a>finally ブロックを使用する方法

例外が発生すると、実行が停止され、コントロールが適切な例外ハンドラーに付与されます。 これは、多くの場合、実行されるはずのコード行がバイパスされることを意味します。 ファイルを閉じるなどのいくつかのリソースのクリーンアップは、例外がスローされた場合でも実行する必要があります。 これを行うために、`finally` ブロックを使用することができます。 `finally` ブロックは、例外がスローされるかどうかに関係なく、常に実行されます。

次のコード例では、`try`/`catch` ブロックを使用して @System.ArgumentOutOfRangeException. をキャッチします。`Main` の方法は 2 つの配列を作成し、　片方をもう一方にコピーしようと試みます。 アクションが、@System.ArgumentOutOfRangeException を生成し、エラーは、コンソールに書き込まれます。 `finally` ブロックは、コピー操作の結果に関係なく実行されます。

C#
```
using System;

class ArgumentOutOfRangeExample
{
    public static void Main()
    {
        int[] array1 = {0, 0};
        int[] array2 = {0, 0};

        try
        {
            Array.Copy(array1, array2, -1);
        }
        catch (ArgumentOutOfRangeException e)
        {
            Console.WriteLine("Error: {0}", e);
        }
        finally
        {
            Console.WriteLine("This statement is always executed.");
        }
    }
}
```

## <a name="how-to-explicitly-throw-exceptions"></a>例外を明示的にスローする方法

`throw` ステートメントを使用して、例外を明示的にスローできます。 `throw` ステートメントを使って、キャッチした例外をもう一度スローすることもできます。 再スローされる例外に情報を追加して、デバッグ時により多くの情報を提供するコーディング手法をお勧めします。

次のコード例は `try`/`catch` ブロックを使い、@System.IO.FileNotFoundException. だと思われるものをキャッチします。次の `try` ブロックは、@System.IO.FileNotFoundException をキャッチし、データ ファイルが見つからない場合に、メッセージをコンソールに出力する `catch` ブロックです。 次のステートメントは、新しい @System.IO.FileNotFoundException をスローして、テキスト情報を例外に追加する `throw` ステートメントです。

C#
```
using System;
using System.IO;

public class ProcessFile
{
   public static void Main()
      {
      FileStream fs = null;
      try   
      {
         //Opens a text tile.
         fs = new FileStream(@"C:\temp\data.txt", FileMode.Open);
         StreamReader sr = new StreamReader(fs);
         string line;

         //A value is read from the file and output to the console.
         line = sr.ReadLine();
         Console.WriteLine(line);
      }
      catch(FileNotFoundException e)
      {
         Console.WriteLine("[Data File Missing] {0}", e);
         throw new FileNotFoundException(@"[data.txt not in c:\temp directory]",e);
      }
      finally
      {
         if (fs != null)
            fs.Dispose();
      }
   }
}
```

## <a name="how-to-create-user-defined-exceptions"></a>ユーザー定義の例外を作成する方法

.NET 基本クラス @System.Exception. から最終的に派生した例外クラスの階層構造を提供します。ただし、定義済みの例外のいずれも要件を満たさない場合は、@System.Exception クラスから派生することによって、独自の例外クラスを作成できます。

独自の例外を作成するときに、ユーザー定義の例外のクラス名の末尾に "Exception" という単語を付加し、次の例で示すように、3 つの共通コンストラクターを実装します。 例では、`EmployeeListNotFoundException` という名前の新しい例外クラスを定義します。 このクラスは @System.Exception から派生し、次の 3 つのコンストラクターが含まれています。

C#
```
using System;

public class EmployeeListNotFoundException: Exception
{
    public EmployeeListNotFoundException()
    {
    }

    public EmployeeListNotFoundException(string message)
        : base(message)
    {
    }

    public EmployeeListNotFoundException(string message, Exception inner)
        : base(message, inner)
    {
    }
}
```

> [!NOTE]
> リモート処理を使用している場合は、任意のユーザー定義の例外のメタデータがサーバー側 (呼び出し先) とクライアント (プロキシ オブジェクトまたは呼び出し元) で使用できることを保証する必要があります。 詳細については、「[例外の推奨事項](#best-practices-for-exceptions)」を参照してください。

## <a name="best-practices-for-exceptions"></a>例外の推奨事項

適切にデザインされたアプリケーションは、アプリケーションのクラッシュを防ぐために、例外やエラーを処理します。 このセクションでは、例外の処理と作成のためのベスト プラクティスについて説明します。

### <a name="use-trycatchfinally-blocks"></a>try/catch/finally ブロックを使用する

`try`/`catch`/`finally` ブロックを使用して、例外を生成する可能性のあるコードを囲みます。 

`catch` ブロックでは、常に特定の例外から一般的な例外の順に例外を配置します。

回復できるかどうかに関わらず、`finally` ブロックを使用してリソースをクリーンアップします。

### <a name="handle-common-conditions-without-throwing-exceptions"></a>例外をスローせずに一般的な状態を処理する

発生する可能性があり、例外をトリガーする可能性がある状態に対し、例外を回避する方法で処理することを検討します。 たとえば、既に終了している接続を終了しようとすると、`InvalidOperationException` を受け取ります。 `if` ステートメントを使用して、終了しようとする前に接続状態を確認することで、これを回避することができます。

C#
```
if (conn.State != ConnectionState.Closed)
{
    conn.Close();
}
```

終了する前に接続状態を確認しない場合は、`InvalidOperationException` 例外をキャッチする可能性があります。

C#
```
try
{
    conn.Close();
}
catch (InvalidOperationException ex)
{
    Console.WriteLine(ex.GetType().FullName);
    Console.WriteLine(ex.Message);
}
```

選択するメソッドは、予期されるイベント発生頻度によって決まります。

- イベントが頻繁には発生しない場合、つまり、イベントが本当に例外的であり、エラー (予期しないファイルの終端の検出など) を示す場合に、例外処理を使用します。 例外処理を使用すると、通常の状況では、実行されるコードが少なくなります。

- イベントが定期的に発生し、通常の実行の一部であると見なせる場合は、コード内でエラー条件をチェックします。 一般的なエラー条件をチェックするときに、例外を回避するためにより少ないコードが実行されます。

### <a name="design-classes-so-that-exceptions-can-be-avoided"></a>例外を回避するようにクラスを設計する

クラスは、例外をトリガーする呼び出しを行うことを回避できるようにするメソッドとプロパティを提供できます。 たとえば、@System.IO.FileStream クラスには、ファイルの終端に到達したかどうかを判別するために役立つメソッドが用意されています。 これらは、ファイルの終端を越えて読み取りを実行しようとした場合にも例外がスローされないようにするために使用できます。 次の例では、例外をトリガーすることなく、ファイルの末尾まで読み取る方法を示します。

C#
```
class FileRead
{
    public void ReadAll(FileStream fileToRead)
    {
        // This if statement is optional
        // as it is very unlikely that
        // the stream would ever be null.
        if (fileToRead == null)
        {
            throw new System.ArgumentNullException();
        }

        int b;

        // Set the stream position to the beginning of the file.
        fileToRead.Seek(0, SeekOrigin.Begin);

        // Read each byte to the end of the file.
        for (int i = 0; i < fileToRead.Length; i++)
        {
            b = fileToRead.ReadByte();
            Console.Write(b.ToString());
            // Or do something else with the byte.
        }
    }
}
```

例外が返されるのを回避するもう 1 つの方法は、非常に一般的なエラーの場合に、例外をスローする代わりに null を返すことです。 非常に一般的なエラーは、通常の制御の流れと見なすことができます。 このような場合は、null を返すことによって、アプリケーションのパフォーマンスへの影響を最小限に抑えることができます。

### <a name="throw-exceptions-instead-of-returning-an-error-code"></a>エラー コードを返す代わりに、例外をスローする

呼び出しのコードはリターン コードを確認しないので、例外によって、エラーを見過ごさないようにします。 

### <a name="use-the-predefined-net-exception-types"></a>事前定義済みの .NET の例外の種類を使用する

事前定義の例外クラスが適用されない場合に限り、新しい例外クラスを導入します。 次に例を示します。

- オブジェクトの現在の状態に対して、プロパティの設定またはメソッドの呼び出しが適切でない場合は、@System.InvalidOperationException をスローします。

- @System.ArgumentException 例外または @System.ArgumentException から派生する定義済みのクラスの 1 つをスローします。

### <a name="end-exception-class-names-with-the-word-exception"></a>例外クラス名の末尾に `Exception` という単語を付加する

カスタム例外が必要な場合は、適切に名前を付け、@System.Exception クラスから派生させます。 次に例を示します。

C#
```
public class MyFileNotFoundException : Exception
{
}
```

### <a name="include-three-constructors-in-custom-exception-classes"></a>カスタム例外クラスに 3 つのコンストラクターを含める

独自の例外クラスを作成するときに、少なくとも 3 つの共通コンストラクターを使用します。それらは、既定のコンストラクター、文字列メッセージを受け取るコンストラクター、および文字列メッセージと内部例外を受け取るコンストラクターです。

- 既定の値を使用する @System.Exception.%23ctor,。

- 文字列メッセージを受け取る @System.Exception.%23ctor(System.String),。

- 文字列メッセージと内部例外を受け取る @System.Exception.%23ctor(System.String,System.Exception),。

例については、「[方法: ユーザー定義の例外を作成する](#how-to-create-user-defined-exceptions)」を参照してください。

### <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>コードがリモートで実行されるときに、例外データが利用できるようにする

ユーザー定義例外を作成するときには、リモートで実行されるコードで例外のメタデータを使用できるようにします。 

たとえば、アプリ ドメインを実装する .NET ランタイムでは、アプリ ドメイン間で例外が発生する可能性があります。 アプリ ドメイン A が、例外をスローするコードを実行するアプリ ドメイン B を作成するとします。 アプリ ドメイン A が例外を適切にキャッチして処理するには、アプリ ドメイン B によりスローされた例外が含まれているアセンブリを検出できる必要があります。アプリ ドメイン B が、アプリ ドメイン A のアプリケーション ベースではなく、自身のアプリケーション ベースの下のアセンブリに含まれている例外をスローする場合、アプリ ドメイン A は、例外を検出できなくなり、共通言語ランタイムが @System.IO.FileNotFoundException 例外をスローします。 このような状況を回避するには、例外情報が格納されているアセンブリを次のいずれかの方法で配置します。

- 2 つのアプリ ドメインが共有する共通アプリケーション ベースにアセンブリを配置する。

    \- または

- ドメインが共通アプリケーション ベースを共有していない場合には、例外情報が格納されているアセンブリに厳密な名前で署名し、グローバル アセンブリ キャッシュにこのアセンブリを配置する。

### <a name="include-a-localized-description-string-in-every-exception"></a>すべての例外に、ローカライズした説明文字列を含める

ユーザーに対して表示されるエラー メッセージは、例外クラスの名前ではなく、スローされた例外の説明文字列から派生されます。

### <a name="use-grammatically-correct-error-messages"></a>文法的に正しいエラー メッセージを使用する

明確な文を記述し、末尾に句点を含めます。 例外の説明文字列の文の末尾には、必ず句点を使用します。 たとえば、"ログ テーブルがオーバーフローしました。" は、 適切な説明文字列です。

### <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>カスタム例外で、必要に応じて追加のプロパティを提供する

プログラミングの点で追加情報が役立つ場合にだけ、(説明文字列以外の) 例外の追加プロパティを含めてください。 たとえば、@System.IO.FileNotFoundException には @System.IO.FileNotFoundException.FileName プロパティがあります。

### <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>スタック トレースが役に立つように throw ステートメントを配置する

例外がスローされたステートメントからスタック トレースが開始され、例外をキャッチした `catch` ステートメントでトレースが終了します。

### <a name="use-exception-builder-methods"></a>例外ビルダー メソッドを使用する

一般に、クラスはクラス実装内の複数の位置で同一の例外をスローします。 コードが長くなることを防ぐため、例外を作成して返すヘルパー メソッドを使用します。 例:

C#
```
class FileReader
{
    private string fileName;

    public FileReader(string path)
    {
        fileName = path;
    }

    public byte[] Read(int bytes)
    {
        byte[] results = FileUtils.ReadFromFile(fileName, bytes);
        if (results == null)
        {
            throw NewFileIOException();
        }
        return results;
    }

    FileReaderException NewFileIOException()
    {
        string description = "My NewFileIOException Description";

        return new FileReaderException(description);
    }
}

```

場合によっては、例外のコンストラクターを使用して例外を作成する方が適切な場合もあります。 @System.ArgumentException, などのグローバル例外クラスはその一例です。 

### <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>例外をスローするときに、中間結果を削除する

呼び出し元が、メソッドから例外がスローされるときに副作用が発生しないと仮定できる必要があります。 たとえば、ある口座から現金を引き出して別の口座に預金することで送金を行うコードがあって、預金の実行中に例外がスローされた場合、引き出しが有効のままにしておきたくはないはずです。

C#
```
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

この状況に対処する方法の 1 つは、預金トランザクションによってスローされた例外をキャッチし、引き出しをロールバックすることです。

C#
```
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw
    }
}
```

この例では、`throw` を使用して、元の例外を再スローすることを示しています。これにより、呼び出し元が @System.Exception.InnerException プロパティを確認することなく、問題の本当の原因を容易に確認できるようになります。 別の方法は、新しい例外をスローして元の例外を内部例外として含めることです。

C#
```
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>参照

.NET での例外の動作の詳細については、「[What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md)」(ランタイム時の例外についてすべての開発者が知っておくべきこと) を参照してください。



<!--HONumber=Nov16_HO3-->


