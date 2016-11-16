---
title: "正規表現に関するベスト プラクティス"
description: "正規表現に関するベスト プラクティス"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 00c7228c5cb906f41df5e60a318721008ecf0bb7

---

# <a name="best-practices-for-regular-expressions"></a>正規表現に関するベスト プラクティス

.NET の正規表現エンジンは、リテラル テキストの比較と照合ではなくパターン一致に基づいてテキストを処理する、完全な機能を備えた強力なツールです。 ほとんどの場合は、すばやく効率的にパターン一致が実行されますが、 処理が非常に遅く見えることもあります。 極端なケースでは、比較的小さな入力の処理に何時間も何日もかかり、応答しなくなったように見えることさえあります。 

ここでは、正規表現で最適なパフォーマンスを確保するためのいくつかのベスト プラクティスの概要を説明します。 このチュートリアルは、次のセクションで構成されています。

* [入力ソースを考慮に入れる](#consider-the-input-source)

* [オブジェクトのインスタンス化を適切に処理する](#handle-object-instantiation-appropriately)

* [バックトラッキングを管理する](#take-charge-of-backtracking)

* [タイムアウト値を使用する](#use-time-out-values)

* [必要なときにのみキャプチャする](#capture-only-when-necessary)

* [関連トピック](#related-topics)

## <a name="consider-the-input-source"></a>入力ソースを考慮に入れる

一般に、正規表現で受け入れられる入力には、制約のある入力と制約のない入力の 2 種類があります。 制約のある入力とは、あらかじめ定義された形式に従っている、既知のソースまたは信頼できるソースからのテキストです。 制約のない入力とは、あらかじめ定義された形式や予想される形式に従っていない可能性のある、不確実なソース (Web ユーザーなど) からのテキストです。

正規表現パターンは、有効な入力に一致するように記述されるのが一般的です。 開発者はまず、対象となるテキストを調査して、そのテキストに一致する正規表現パターンを記述します。 記述が完了すると、そのパターンを複数の有効な入力項目でテストして、修正や改善が必要かどうかを確認します。 想定されるすべての有効な入力に一致するようになったら、そのパターンは運用環境で使用する準備が整ったと見なされ、リリースされるアプリケーションに含めることができます。 こうして作成された正規表現パターンは、制約のある入力との照合には適していますが、 制約のない入力との照合に適しているとは言えません。

制約のない入力と照合する正規表現は、次の 3 種類のテキストを効率的に処理できなければなりません。

• 正規表現パターンに一致するテキスト。

• 正規表現パターンに一致しないテキスト。

• 正規表現パターンにほぼ一致するテキスト。

制約のある入力を処理するために記述された正規表現で特に問題となるのは、最後の種類のテキストです。 その正規表現が広範な[バックトラッキング](backtracking.md)にも依存している場合、一見何の問題もないように見えるテキストの処理に極端に長い時間 (場合によっては何時間も何日も) が費やされる可能性があります。 

> [!WARNING]
> 次の例では、過度なバックトラッキングを生じる傾向があり、有効な電子メール アドレスを拒否する可能性がある正規表現を使用します。 電子メールの検証ルーチンで使用しないでください。 メール アドレスを検証する正規表現が必要な場合は、「[方法: 文字列が有効な電子メール形式であるかどうかを検証する](verify-format.md)」を参照してください。 


例として、電子メール アドレスのエイリアスを検証するための正規表現について見てみましょう。このような正規表現はよく使用されますが、きわめて大きな問題もはらんでいます。 有効と見なされる電子メール アドレスを処理するために、`^[0-9A-Z]([-.\w]*[0-9A-Z])*$` という正規表現を記述したとします。有効な電子メール アドレスは、英数字で始まり、その後に 0 個以上の文字 (英数字、ピリオド、またはハイフン) が続きます。 また、正規表現は英数字で終了する必要があります。 この正規表現は、次の例に示すように、有効な入力は簡単に処理できますが、有効に近い入力を処理するときに極端に処理効率が低下します。

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      Stopwatch sw;    
      string[] addresses = { "AAAAAAAAAAA@contoso.com", 
                             "AAAAAAAAAAaaaaaaaaaa!@contoso.com" };
      // The following regular expression should not actually be used to 
      // validate an email address.
      string pattern = @"^[0-9A-Z]([-.\w]*[0-9A-Z])*$";
      string input; 

      foreach (var address in addresses) {
         string mailBox = address.Substring(0, address.IndexOf("@"));       
         int index = 0;
         for (int ctr = mailBox.Length - 1; ctr >= 0; ctr--) {
            index++;

            input = mailBox.Substring(ctr, index); 
            sw = Stopwatch.StartNew();
            Match m = Regex.Match(input, pattern, RegexOptions.IgnoreCase);
            sw.Stop();
            if (m.Success)
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed);
            else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed);
         }
         Console.WriteLine();
      }
   }
}

// The example displays output similar to the following:
//     1. Matched '                        A' in 00:00:00.0007122
//     2. Matched '                       AA' in 00:00:00.0000282
//     3. Matched '                      AAA' in 00:00:00.0000042
//     4. Matched '                     AAAA' in 00:00:00.0000038
//     5. Matched '                    AAAAA' in 00:00:00.0000042
//     6. Matched '                   AAAAAA' in 00:00:00.0000042
//     7. Matched '                  AAAAAAA' in 00:00:00.0000042
//     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
//     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
//    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
//    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
//    
//     1. Failed  '                        !' in 00:00:00.0000447
//     2. Failed  '                       a!' in 00:00:00.0000071
//     3. Failed  '                      aa!' in 00:00:00.0000071
//     4. Failed  '                     aaa!' in 00:00:00.0000061
//     5. Failed  '                    aaaa!' in 00:00:00.0000081
//     6. Failed  '                   aaaaa!' in 00:00:00.0000126
//     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
//     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
//     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
//    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
//    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
//    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
//    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
//    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
//    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
//    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
//    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
//    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
//    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
//    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
//    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim sw As Stopwatch    
      Dim addresses() As String = { "AAAAAAAAAAA@contoso.com", 
                                 "AAAAAAAAAAaaaaaaaaaa!@contoso.com" }
      ' The following regular expression should not actually be used to 
      ' validate an email address.
      Dim pattern As String = "^[0-9A-Z]([-.\w]*[0-9A-Z])*$"
      Dim input As String 

      For Each address In addresses
         Dim mailBox As String = address.Substring(0, address.IndexOf("@"))       
         Dim index As Integer = 0
         For ctr As Integer = mailBox.Length - 1 To 0 Step -1
            index += 1
            input = mailBox.Substring(ctr, index) 
            sw = Stopwatch.StartNew()
            Dim m As Match = Regex.Match(input, pattern, RegexOptions.IgnoreCase)
            sw.Stop()
            if m.Success Then
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed)
            Else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed)
            End If                  
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays output similar to the following:
'     1. Matched '                        A' in 00:00:00.0007122
'     2. Matched '                       AA' in 00:00:00.0000282
'     3. Matched '                      AAA' in 00:00:00.0000042
'     4. Matched '                     AAAA' in 00:00:00.0000038
'     5. Matched '                    AAAAA' in 00:00:00.0000042
'     6. Matched '                   AAAAAA' in 00:00:00.0000042
'     7. Matched '                  AAAAAAA' in 00:00:00.0000042
'     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
'     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
'    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
'    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
'    
'     1. Failed  '                        !' in 00:00:00.0000447
'     2. Failed  '                       a!' in 00:00:00.0000071
'     3. Failed  '                      aa!' in 00:00:00.0000071
'     4. Failed  '                     aaa!' in 00:00:00.0000061
'     5. Failed  '                    aaaa!' in 00:00:00.0000081
'     6. Failed  '                   aaaaa!' in 00:00:00.0000126
'     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
'     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
'     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
'    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
'    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
'    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
'    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
'    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
'    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
'    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
'    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
'    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
'    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
'    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
'    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

この出力を見るとわかるように、有効な電子メール エイリアスは、その長さに関係なくほとんど同じ時間で処理されます。 一方、有効に近い電子メール アドレスでは、長さが 5 文字を超えると、文字列の文字が 1 文字増えるたびに処理時間が約 2 倍に増加します。 つまり、有効に近い文字列の長さが 28 文字になると処理に 1 時間以上かかり、33 文字になるとほぼ 1 日かかることになります。 

この正規表現は、一致する入力の形式ばかりを念頭に置いて開発されていて、パターンに一致しない入力のことが考慮されていません。 そのため、制約のない入力が正規表現パターンにほぼ一致する場合に、パフォーマンスが大幅に低下する可能性があります。

この問題を解決する方法を以下に示します。

* パターンを開発するときには、バックトラッキングが正規表現エンジンのパフォーマンスに与える影響を考慮に入れます。特に、制約のない入力を処理する正規表現ではこれが重要です。 詳細については、このトピックの「[バックトラッキングを管理する](#take-charge-of-backtracking)」を参照してください。

* 有効な入力だけでなく、無効な入力と有効に近い入力も使用して、正規表現を徹底的にテストします。 特定の正規表現に対する入力をランダムに生成するには、Microsoft Research の正規表現調査ツール [Rex](http://research.microsoft.com/en-us/projects/rex/) を使用できます。

## <a name="handle-object-instantiation-appropriately"></a>オブジェクトのインスタンス化を適切に処理する

.NET の正規表現オブジェクト モデルの中核となるのは、正規表現エンジンを表す [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) クラスです。 [Regex](xref:System.Text.RegularExpressions.Regex) エンジンの使用方法は、多くの場合、正規表現のパフォーマンスを左右する最大の要因になります。 正規表現を定義するときには、正規表現エンジンと正規表現パターンを密に結合する必要があります。 この結合のプロセスは、正規表現パターンをコンストラクターに渡して [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化する場合も、分析する文字列と共に正規表現パターンを渡して静的メソッドを呼び出す場合も、必然的にコストが高くなります。

正規表現エンジンを特定の正規表現パターンと結合し、そのエンジンを使用してテキストを照合するには、次のようにいくつかの方法があります。

* パターン一致を実行する静的メソッド [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) などを呼び出します。 この場合は、正規表現オブジェクトをインスタンス化する必要はありません。

* [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化し、解釈される正規表現のパターン一致を実行するインスタンス メソッドを呼び出します。 これは、正規表現エンジンを正規表現パターンにバインドするための既定の方法です。 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) フラグを含むオプション引数を使用せずに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトがインスタンス化された場合にこのようになります。

* [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化し、コンパイルされた正規表現のパターン一致を実行するインスタンス メソッドを呼び出します。 [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化するときに、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) フラグを含むオプション引数を指定した場合、正規表現オブジェクトはコンパイル済みのパターンを表します。

> [!IMPORTANT]
> メソッド呼び出しの形式 (静的、解釈、コンパイル) は、メソッド呼び出しで同じ正規表現が繰り返し使用される場合や、アプリケーションで正規表現オブジェクトが多用される場合に、パフォーマンスに影響を与えます。
 
### <a name="static-regular-expressions"></a>静的正規表現

静的正規表現メソッドは、正規表現オブジェクトを同じ正規表現で繰り返しインスタンス化する代わりの方法として推奨されます。 正規表現オブジェクトで使用される正規表現パターンとは異なり、インスタンス メソッドの呼び出しで使用されるパターンの場合は、そのオペレーション コードまたはコンパイルされた Microsoft Intermediate Language (MSIL) が正規表現エンジンによって内部にキャッシュされます。 

たとえば、ユーザー入力を検証するメソッドを呼び出すことができます。 この例では `IsValidCurrency` という名前のメソッドが、ユーザーが少なくとも 1 つの 10 進数を通貨記号の後に入力したかどうかを確認します。 次の例は、`IsValidCurrency` メソッドのきわめて非効率的な実装を示しています。 この例では、このメソッドが呼び出されるたびに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトが同じパターンでインスタンス化されます。 そのため、メソッドが呼び出されるたびに正規表現パターンを再コンパイルしなければならなくなります。

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      Regex currencyRegex = new Regex(pattern);
      return currencyRegex.IsMatch(currencyValue);
   }
}
```

```vb
Public Sub OKButton_Click(sender As Object, e As EventArgs) _ 
           Handles OKButton.Click

   If Not String.IsNullOrEmpty(sourceCurrency.Text) Then
      If RegexLib.IsValidCurrency(sourceCurrency.Text) Then
         PerformConversion()
      Else
         status.Text = "The source currency value is invalid."
      End If          
   End If
End Sub
```

この非効率的なコードは、静的な [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) メソッドの呼び出しに置き換える必要があります。 これにより、パターン一致メソッドを呼び出すたびに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化する必要がなくなり、正規表現エンジンがキャッシュからコンパイル済みの正規表現を取得できるようになります。

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      return Regex.IsMatch(currencyValue, pattern); 
   }
}
```

```vb
Imports System.Text.RegularExpressions

Public Module RegexLib
   Public Function IsValidCurrency(currencyValue As String) As Boolean
      Dim pattern As String = "\p{Sc}+\s*\d+"
      Return Regex.IsMatch(currencyValue, pattern)
   End Function
End Module
```

既定では、最近使用された静的正規表現パターンが 15 個までキャッシュされます。 アプリケーションで多数の静的正規表現をキャッシュする必要がある場合は、[Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) プロパティを設定してキャッシュのサイズを調整できます。

この例で使用されている正規表現 `\p{Sc}+\s*\d+` は、入力文字列が通貨記号と 1 文字以上の 10 進数の数字で構成されているかどうかを確認します。 このパターンは、次の表に示すように定義されます。

パターン | 説明
------- | -----------
`\p{Sc}+` | Unicode の Symbol, Currency カテゴリの 1 個以上の文字と一致します。
`\s*` | 0 個以上の空白文字と一致します。
`\d+` | 1 個以上の 10 進数と一致します。
 
### <a name="interpreted-vs-compiled-regular-expressions"></a>解釈される正規表現とコンパイルされる正規表現

[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを指定して正規表現エンジンにバインドされていない正規表現パターンは、解釈されます。 正規表現オブジェクトがインスタンス化されるとき、正規表現エンジンは、その正規表現を一連のオペレーション コードに変換します。 インスタンス メソッドが呼び出されると、オペレーション コードが MSIL に変換され、JIT コンパイラによって実行されます。 同様に、静的正規表現メソッドが呼び出され、その正規表現がキャッシュに見つからない場合、正規表現エンジンは、その正規表現を一連のオペレーション コードに変換し、キャッシュに格納します。 それらのオペレーション コードは、その後、JIT コンパイラで実行できるように MSIL に変換されます。 解釈される正規表現では、実行時間が長くなる代わりに、スタートアップ時間が短縮されます。 このため、正規表現を使用するメソッドの呼び出し回数が少ない場合、または正確な回数はわからなくても少ないと予想される場合に適しています。 メソッド呼び出しの回数が増えるにつれて、スタートアップ時間の短縮というメリットよりも、実行速度の低下というデメリットの方が大きくなります。

[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを指定して正規表現エンジンにバインドされている正規表現パターンは、コンパイルされます。 つまり、正規表現オブジェクトがインスタンス化されるとき、または静的正規表現メソッドが呼び出され、その正規表現がキャッシュに見つからないとき、正規表現エンジンは、その正規表現を一連の中間的なオペレーション コードに変換し、さらに MSIL に変換します。 メソッドが呼び出されると、その MSIL が JIT コンパイラによって実行されます。 コンパイルされる正規表現では、解釈される正規表現とは対照的に、スタートアップ時間が長くなる一方で、個々のパターン一致メソッドの実行時間は短くなります。 結果として、正規表現のコンパイルによって得られるパフォーマンス上のメリットは、正規表現メソッドが呼び出される回数に比例して大きくなります。

要約すると、特定の正規表現について正規表現メソッドを呼び出す回数が比較的少ない場合は、解釈される正規表現を使用することをお勧めします。 特定の正規表現について正規表現メソッドを呼び出す回数が比較的多い場合は、コンパイルされる正規表現を使用することをお勧めします。 解釈される正規表現で実行速度の低下がスタートアップ時間の短縮を上回るしきい値や、コンパイルされる正規表現でスタートアップ時間の増加が実行速度の向上を上回るしきい値については、正確な値を特定するのは困難です。 これは、正規表現の複雑さや、処理される個々のデータなど、さまざまな要因に依存します。 特定のアプリケーションのシナリオにおいて、解釈される正規表現とコンパイルされる正規表現のどちらで最適なパフォーマンスが得られるかを特定するには、[Stopwatch](xref:System.Diagnostics.Stopwatch) クラスを使用して実行時間を比較します。

次の例では、Theodore Dreiser の『The Financier』の最初の 10 個の文を読み取る場合とすべての文を読み取る場合について、コンパイルされる正規表現と解釈される正規表現のパフォーマンスを比較しています。 出力を見るとわかるように、正規表現の一致メソッドの呼び出しが 10 回だけの場合は、解釈される正規表現の方がコンパイルされる正規表現よりパフォーマンスが高くなります。 しかし、多数の呼び出し (この場合は 13,000 回以上) が行われる場合は、コンパイルされる正規表現の方がパフォーマンスが高くなります。 

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]";
      Stopwatch sw;
      Match match;
      int ctr;

      StreamReader inFile = new StreamReader(@".\Dreiser_TheFinancier.txt");
      string input = inFile.ReadToEnd();
      inFile.Close();

      // Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex int10 = new Regex(pattern, RegexOptions.Singleline);
      match = int10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex comp10 = new Regex(pattern, 
                   RegexOptions.Singleline | RegexOptions.Compiled);
      match = comp10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex intAll = new Regex(pattern, RegexOptions.Singleline);
      match = intAll.Match(input);
      int matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);

      // Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex compAll = new Regex(pattern, 
                      RegexOptions.Singleline | RegexOptions.Compiled);
      match = compAll.Match(input);
      matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);      
   }
}
// The example displays the following output:
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0047491
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0141872
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1929928
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7635869
//       
//       >compare1
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0046914
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0143727
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1514100
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7432921
```

```vb
Imports System.Diagnostics
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]"
      Dim sw As Stopwatch
      Dim match As Match
      Dim ctr As Integer

      Dim inFile As New StreamReader(".\Dreiser_TheFinancier.txt")
      Dim input As String = inFile.ReadToEnd()
      inFile.Close()

      ' Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim int10 As New Regex(pattern, RegexOptions.SingleLine)
      match = int10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim comp10 As New Regex(pattern, 
                   RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = comp10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim intAll As New Regex(pattern, RegexOptions.SingleLine)
      match = intAll.Match(input)
      Dim matches As Integer = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)

      ' Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim compAll As New Regex(pattern, 
                     RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = compAll.Match(input)
      matches = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)      
   End Sub
End Module
' The example displays output like the following:
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0047491
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0141872
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1929928
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7635869
'       
'       >compare1
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0046914
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0143727
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1514100
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7432921
```

この例で使用する正規表現パターン `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`\w+` | 1 つ以上の単語文字に一致します。
`(\r?\n)|,?\s)` | 0 ～ 1 個の復帰とそれに続く改行文字、または 0 ～ 1 個のコンマとそれに続く空白文字に一致します。
`(\w+((\r?\n)|,?\s))*` | 1 個以上の単語文字の後に 0 ～ 1 個の復帰と改行文字または 0 ～ 1 個のコンマと空白文字が続くパターンの 0 回以上の出現に一致します。
`\w+` | 1 つ以上の単語文字に一致します。
`[.?:;!]` | ピリオド、疑問符、コロン、セミコロン、または感嘆符に一致します。
 
## <a name="take-charge-of-backtracking"></a>バックトラッキングを管理する

通常、正規表現エンジンは入力文字列内を直線的に進んで、入力文字列を正規表現パターンと比較します。 しかし、正規表現パターン内で不定量指定子 (__*__、**+**、**?** など)  が使用されていると、パターン全体に対する一致を検索するために、それまでに見つかった部分的な一致を放棄して、以前に保存した状態に戻る場合があります。 このプロセスをバックトラッキングと呼びます。

> [!NOTE]
> バックトラッキングの詳細については、「[正規表現の動作の詳細](regex-behavior.md)」と「[正規表現におけるバックトラッキング](backtracking.md)」を参照してください。
 
バックトラッキングのサポートにより、正規表現はより強力かつ柔軟になります。 同時に、正規表現エンジンの動作を正規表現の開発者が制御することにもなります。 この責任を認識していない開発者によるバックトラッキングの誤用や過度なバックトラッキングへの依存が、多くの場合、正規表現のパフォーマンスを低下させる最大の要因になっています。 最悪のシナリオでは、入力文字列が 1 文字増えるたびに実行時間が倍増することもあります。 実際、バックトラッキングを過度に使用すると、入力が正規表現パターンにほぼ一致する場合に、プログラム的に無限ループと同等の状態に陥りやすくなります。そのような状態では、正規表現エンジンによる比較的短い入力文字列の処理に何時間も何日もかかることがあります。

照合に必要でないにもかかわらずバックトラッキングを使用した代償として、アプリケーションのパフォーマンスが低下することもよくあります。 例として、`\b\p{Lu}\w*\b` という正規表現について見てみましょう。この正規表現は、次の表に示すように、大文字で始まるすべての単語に一致します。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`\p{Lu}` | 大文字に一致します。
`\w*` | 0 個以上の単語に使用される文字に一致します。
`\b` | ワード境界で照合を終了します。
 
ワード境界は単語文字と同じではなく、単語文字のサブセットでもないため、正規表現エンジンが単語文字の照合中にワード境界を越える可能性はありません。 したがって、この正規表現では、バックトラッキングが照合の全体的な成功に寄与することはありません。バックトラッキングを使用すると、正規表現エンジンが単語文字の照合に成功するたびに状態を保存しなければならなくなるため、パフォーマンスを低下させるだけです。

バックトラッキングが不要であることがわかった場合は、**(?>**_subexpression_**)** 言語要素を使用して無効にすることができます。 次の例では、2 つの正規表現を使用して入力文字列を解析しています。 1 つはバックトラッキングに依存する `\b\p{Lu}\w*\b`、 もう 1 つはバックトラッキングを無効にする `\b\p{Lu}(?>\w*)\b` です。 出力を見るとわかるように、どちらも結果は同じになります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This this word Sentence name Capital";
      string pattern = @"\b\p{Lu}\w*\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);

      Console.WriteLine();

      pattern = @"\b\p{Lu}(?>\w*)\b";   
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This
//       Sentence
//       Capital
//       
//       This
//       Sentence
//       Capital
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This this word Sentence name Capital"
      Dim pattern As String = "\b\p{Lu}\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
      Console.WriteLine()

      pattern = "\b\p{Lu}(?>\w*)\b"   
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This
'       Sentence
'       Capital
'       
'       This
'       Sentence
'       Capital
```

正規表現パターンと入力テキストの照合にバックトラッキングが欠かせない場合もよくあります。 ただし、過度なバックトラッキングが発生すると、極端にパフォーマンスが低下して、アプリケーションが応答しなくなったように見えることがあります。 この状況が発生するのは、たとえば、量指定子が入れ子になっていて、外側の部分式に一致するテキストが内側の部分式に一致するテキストのサブセットになっている場合です。 

> [!WARNING]
> 過度なバックトラッキングの回避に加えて、タイムアウト機能を使用して、過度なバックトラッキングによって、正規表現のパフォーマンスが極端に低下するのを防ぐ必要があります。 詳細については、「[タイムアウト値を使用する](#use-time-out-values)」を参照してください。
 
例として、部品番号に一致するように作られた `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` という正規表現パターンについて見てみましょう。この部品番号は、少なくとも 1 文字の英数字で構成されます。 追加の文字では、英数字、ハイフン、アンダースコア、およびピリオドが許容されますが、最後の文字は英数字でなければなりません。 部品番号の終わりはドル記号で示されます。 この正規表現パターンは、量指定子が入れ子になっているうえに、部分式 `[0-9A-Z]` が部分式 `[-.\w]*` のサブセットであるため、パフォーマンスが極端に低下する可能性があります。

このような場合に正規表現のパフォーマンスを最適化するには、入れ子になった量指定子を削除して、外側の部分式をゼロ幅の先読みアサーションまたは後読みアサーションに置き換えます。 先読みアサーションと後読みアサーションはアンカーなので、入力文字列内でポインターを移動させることなく、先読みまたは後読みによって、指定された条件が満たされているかどうかを確認します。 たとえば、この部品番号の正規表現は `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$` として書き直すことができます。 この正規表現パターンは、次の表に示すように定義されます。

パターン | 説明
------- | -----------
`^` | 入力文字列の先頭から照合を開始します。
`[0-9A-Z]` | 英数字 1 文字に一致します。 これは、部品番号に最低限必要な文字です。
`[-.\w]*` | 任意の単語文字、ハイフン、またはピリオドの 0 回以上の出現に一致します。
`\$] | ドル記号に一致します。
`(?<=[0-9A-Z])` | 末尾のドル記号を先読みし、前の文字が英数字であることを確認します。
`$` 入力文字列の末尾で照合を終了します。
 
次の例では、この正規表現を使用して、部品番号を含む配列を照合しています。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$";
      string[] partNos = { "A1C$", "A4", "A4$", "A1603D$", "A1603D#" };

      foreach (var input in partNos) {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine(match.Value);
         else
            Console.WriteLine("Match not found.");
      }      
   }
}
// The example displays the following output:
//       A1C$
//       Match not found.
//       A4$
//       A1603D$
//       Match not found.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$"
      Dim partNos() As String = { "A1C$", "A4", "A4$", "A1603D$", 
                                  "A1603D#" }

      For Each input As String In partNos
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine(match.Value)
         Else
            Console.WriteLine("Match not found.")
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       A1C$
'       Match not found.
'       A4$
'       A1603D$
'       Match not found.
```

.NET の正規表現言語には、入れ子になった量指定子を取り除くために使用できる次の言語要素が含まれています。 詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

言語要素 | 説明
---------------- | ----------- 
**(?**=_subexpression_**)** | ゼロ幅の肯定先読みです。 現在の位置からの先読みにより、*subexpression* が入力文字列に一致するかどうかを確認します。
**(?!**_subexpression_**)** | ゼロ幅の否定先読みです。 現在の位置からの先読みにより、*subexpression* が入力文字列に一致しないかどうかを確認します。
**(?<**=_subexpression_**)** | ゼロ幅の肯定後読みです。 現在の位置からの後読みにより、*subexpression* が入力文字列に一致するかどうかを確認します。
**(?<!**_subexpression_**)** | ゼロ幅の否定後読みです。 現在の位置からの後読みにより、*subexpression* が入力文字列に一致しないかどうかを確認します。
 
## <a name="use-timeout-values"></a>タイムアウト値を使用する

正規表現が正規表現パターンにほぼ一致する入力を処理する場合は、パフォーマンスに大きな影響を与える過度なバックトラッキングに依存することがよくあります。 慎重にバックトラッキングの使用を検討し、ほぼ一致する入力に対して正規表現をテストすることに加えて、過度なバックトラッキングが発生した場合にその影響を確実に最小限に抑えるために、必ずタイムアウト値を設定する必要があります。

正規表現のタイムアウト間隔は、タイムアウトする前に正規表現エンジンが単一の一致を検索する期間を定義します。 既定のタイムアウト間隔は [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout) で、正規表現がタイムアウトしないことを意味します。 次のようにこの値をオーバーライドし、タイムアウト間隔を定義できます。 

* [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) コンストラクターを呼び出すことによって、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化するときに、タイムアウト値を指定します。

* [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan))、[Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) など、*matchTimeout* パラメーターを含む静的パターン一致メソッドを呼び出します。

タイムアウト間隔を定義していて、その間隔の終了時に一致が見つからない場合、正規表現メソッドは [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) 例外をスローします。 例外ハンドラーで、タイムアウト間隔を延長して一致を再試行する、一致操作を破棄して一致なしと見なす、または一致操作を破棄して今後の分析のために例外情報を記録することを選択できます。

次の例では、テキスト ドキュメントの単語の数と 1 つの単語に含まれる平均文字数を計算するために、タイムアウト間隔が 350 ミリ秒の正規表現をインスタンス化する `GetWordData` メソッドを定義します。 一致操作がタイムアウトした場合、タイムアウト間隔は 350 ミリ秒ずつ延長され、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトが再インスタンス化されます。 新しいタイムアウト間隔が 1 秒を超える場合、メソッドは呼び出し元に例外を再スローします。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string title = "Doyle - The Hound of the Baskervilles.txt";
      try {
         var info = util.GetWordData(title);
         Console.WriteLine("Words:               {0:N0}", info.Item1);
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2); 
      }
      catch (IOException e) {
         Console.WriteLine("IOException reading file '{0}'", title);
         Console.WriteLine(e.Message);
      }
      catch (RegexMatchTimeoutException e) {
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds);
      }
   }
}

public class RegexUtilities
{
   public Tuple<int, double> GetWordData(string filename)
   { 
      const int MAX_TIMEOUT = 1000;   // Maximum timeout interval in milliseconds.
      const int INCREMENT = 350;      // Milliseconds increment of timeout.

      List<string> exclusions = new List<string>( new string[] { "a", "an", "the" });
      int[] wordLengths = new int[29];        // Allocate an array of more than ample size.
      string input = null;
      StreamReader sr = null;
      try { 
         sr = new StreamReader(filename);
         input = sr.ReadToEnd();
      }
      catch (FileNotFoundException e) {
         string msg = String.Format("Unable to find the file '{0}'", filename);
         throw new IOException(msg, e);
      }
      catch (IOException e) {
         throw new IOException(e.Message, e);
      }
      finally {
         if (sr != null) sr.Close(); 
      }

      int timeoutInterval = INCREMENT;
      bool init = false;
      Regex rgx = null;
      Match m = null;
      int indexPos = 0;  
      do {
         try {
            if (! init) {
               rgx = new Regex(@"\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval));
               m = rgx.Match(input, indexPos);
               init = true;
            }
            else { 
               m = m.NextMatch();
            }
            if (m.Success) {    
               if ( !exclusions.Contains(m.Value.ToLower()))
                  wordLengths[m.Value.Length]++;

               indexPos += m.Length + 1;   
            }
         }
         catch (RegexMatchTimeoutException e) {
            if (e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT) {
               timeoutInterval += INCREMENT;
               init = false;
            }
            else {
               // Rethrow the exception.
               throw; 
            }   
         }          
      } while (m.Success);

      // If regex completed successfully, calculate number of words and average length.
      int nWords = 0; 
      long totalLength = 0;

      for (int ctr = wordLengths.GetLowerBound(0); ctr <= wordLengths.GetUpperBound(0); ctr++) {
         nWords += wordLengths[ctr];
         totalLength += ctr * wordLengths[ctr];
      }
      return new Tuple<int, double>(nWords, totalLength/nWords);
   }
}
```

```vb
Imports System.Collections.Generic
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim util As New RegexUtilities()
      Dim title As String = "Doyle - The Hound of the Baskervilles.txt"
      Try
         Dim info = util.GetWordData(title)
         Console.WriteLine("Words:               {0:N0}", info.Item1)
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2) 
      Catch e As IOException
         Console.WriteLine("IOException reading file '{0}'", title)
         Console.WriteLine(e.Message)
      Catch e As RegexMatchTimeoutException
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds)
      End Try
   End Sub
End Module

Public Class RegexUtilities
   Public Function GetWordData(filename As String) As Tuple(Of Integer, Double) 
      Const MAX_TIMEOUT As Integer = 1000  ' Maximum timeout interval in milliseconds.
      Const INCREMENT As Integer = 350     ' Milliseconds increment of timeout.

      Dim exclusions As New List(Of String)({"a", "an", "the" })
      Dim wordLengths(30) As Integer        ' Allocate an array of more than ample size.
      Dim input As String = Nothing
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader(filename)
         input = sr.ReadToEnd()
      Catch e As FileNotFoundException
         Dim msg As String = String.Format("Unable to find the file '{0}'", filename)
         Throw New IOException(msg, e)
      Catch e As IOException
         Throw New IOException(e.Message, e)
      Finally
         If sr IsNot Nothing Then sr.Close() 
      End Try

      Dim timeoutInterval As Integer = INCREMENT
      Dim init As Boolean = False
      Dim rgx As Regex = Nothing
      Dim m As Match = Nothing
      Dim indexPos As Integer = 0  
      Do
         Try
            If Not init Then
               rgx = New Regex("\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval))
               m = rgx.Match(input, indexPos)
               init = True
            Else 
               m = m.NextMatch()
            End If
            If m.Success Then    
               If Not exclusions.Contains(m.Value.ToLower()) Then
                  wordLengths(m.Value.Length) += 1
               End If
               indexPos += m.Length + 1   
            End If
         Catch e As RegexMatchTimeoutException
            If e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT Then
               timeoutInterval += INCREMENT
               init = False
            Else
               ' Rethrow the exception.
               Throw 
            End If   
         End Try          
      Loop While m.Success

      ' If regex completed successfully, calculate number of words and average length.
      Dim nWords As Integer
      Dim totalLength As Long

      For ctr As Integer = wordLengths.GetLowerBound(0) To wordLengths.GetUpperBound(0)
         nWords += wordLengths(ctr)
         totalLength += ctr * wordLengths(ctr)
      Next
      Return New Tuple(Of Integer, Double)(nWords, totalLength/nWords)
   End Function
End Class
```

## <a name="capture-only-when-necessary"></a>必要なときにのみキャプチャする

.NET の正規表現では、数多くのグループ化構成体がサポートされています。これらを使用すると、正規表現パターンを 1 つ以上の部分式にグループ化することができます。 .NET の正規表現言語で最もよく使用されるグループ化構成体は、番号付きのキャプチャ グループを定義する **(**_subexpression_**)** と、名前付きのキャプチャ グループを定義する **(?<*_name_**>**_subexpression_**)** です。 グループ化構成体は、前方参照を作成したり、量指定子を適用する部分式を定義したりするのに欠かせません。 

しかし、これらの言語要素の使用にはコストが伴います。 まず、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティから返される [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトに、最新の名前のないキャプチャまたは名前付きキャプチャが設定されます。また、1 つのグループ化構成体によって入力文字列の複数の部分文字列がキャプチャされた場合は、特定のキャプチャ グループの [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) プロパティから返される [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトに複数の [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトが設定されます。

正規表現内で量指定子を適用できるようにするためだけにグループ化構成体が使用されていて、それらの部分式によってキャプチャされたグループがその後に使用されていない場合もよくあります。 例として、文全体をキャプチャするために作られた正規表現 `\b(\w+[;,]?\s?)+[.?!]` について見てみましょう。 次の表は、この正規表現パターン内の言語要素と、[Match](xref:System.Text.RegularExpressions.Match) オブジェクトの [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) コレクションおよび [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) コレクションに対する影響を示しています。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`\w+` | 1 つ以上の単語文字に一致します。
`[;,]?` | 0 個または 1 個のコンマまたはセミコロンに一致します。
`\s?` | 0 個または 1 個の空白文字と一致します。
`(\w+[;,]?\s?)+` | 1 個以上の単語文字の後に省略可能なコンマまたはセミコロンと省略可能な空白文字が続くパターンの 1 回以上の出現に一致します。 これにより、最初のキャプチャ グループが定義されます。このグループは、複数の単語文字の組み合わせ (つまり単語) の後に省略可能な区切り記号が続くパターンが、正規表現エンジンが文の終わりに到達するまで繰り返されるようにするために必要です。
`[.?!]` | ピリオド、疑問符、または感嘆符に一致します。
 
次の例に示すように、一致が見つかると、[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトと [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトの両方に一致からのキャプチャが設定されます。 ここでは、**+** 量指定子を適用できるようにするためにキャプチャ グループ `(\w+[;,]?\s?)` が使用されているため、正規表現パターンが文の各単語に一致します。 そうでない場合は、文の最後の単語に一致します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//          Group 1: 'sentence' at index 12.
//             Capture 0: 'This ' at 0.
//             Capture 1: 'is ' at 5.
//             Capture 2: 'one ' at 8.
//             Capture 3: 'sentence' at 12.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
//          Group 1: 'another' at index 30.
//             Capture 0: 'This ' at 22.
//             Capture 1: 'is ' at 27.
//             Capture 2: 'another' at 30.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'          Group 1: 'sentence' at index 12.
'             Capture 0: 'This ' at 0.
'             Capture 1: 'is ' at 5.
'             Capture 2: 'one ' at 8.
'             Capture 3: 'sentence' at 12.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
'          Group 1: 'another' at index 30.
'             Capture 0: 'This ' at 22.
'             Capture 1: 'is ' at 27.
'             Capture 2: 'another' at 30.
```

量指定子を適用するためだけに部分式を使用していて、キャプチャされたテキストは特に必要ないという場合は、グループ キャプチャを無効にする必要があります。 たとえば、**(?:**_subexpression_**)** 言語要素をグループに適用すると、そのグループでは、一致した部分文字列がキャプチャされなくなります。 次の例では、前の例の正規表現パターンが `\b(?:\w+[;,]?\s?)+[.?!]` に変更されています。 出力を見るとわかるように、これにより、[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) コレクションと [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) コレクションが設定されなくなります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(?:\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(?:\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
```

キャプチャを無効にするには次のような方法があります。

* **(?:**_subexpression_**)** 言語要素を使用します。 この要素をグループに適用すると、そのグループでは、一致した部分文字列がキャプチャされなくなります。 入れ子になったグループによる部分文字列のキャプチャは無効になりません。

* [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) オプションを使用します。 これにより、正規表現パターン内の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。 このオプションを使用した場合は、**(?<**_name_**>**_subexpression_**)** 言語要素を使用して定義した名前付きグループに一致する部分文字列のみがキャプチャされます。 [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) フラグは、[Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターの options パラメーターか、[Regex](xref:System.Text.RegularExpressions.Regex) の静的な一致メソッドの options パラメーターに渡すことができます。

* **(?imnsx)** 言語要素の **n** オプションを使用します。 これにより、正規表現パターンでこの要素が出現する位置以降の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。 パターンの末尾に到達するか、**(-n)** オプションによって名前のないキャプチャ (暗黙的なキャプチャ) が有効になるまで、キャプチャは無効のままです。 詳細については、「[正規表現でのその他の構成体](miscellaneous.md)」を参照してください。

* **(?imnsx:**_subexpression_**)** 言語要素の **n** オプションを使用します。 これにより、*subexpression* 内の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。 入れ子になった名前のない (暗黙的な) キャプチャ グループによるキャプチャも無効になります。

## <a name="related-topics"></a>関連トピック

タイトル | 説明
----- | ----------- 
[正規表現の動作の詳細](regex-behavior.md) | .NET の正規表現エンジンの実装について検討します。 正規表現の柔軟性に焦点を当てて、正規表現エンジンの効率的かつ堅牢な動作を確保するための開発者の責任について説明します。
[正規表現におけるバックトラッキング](backtracking.md) | バックトラッキングの概要と、正規表現のパフォーマンスに与える影響について説明し、バックトラッキングの代わりに使用できる言語要素について検討します。
[正規表現言語 - クイック リファレンス](quick-ref.md) | .NET の正規表現言語の言語要素について説明します。各言語要素の詳細な説明へのリンクも含まれています。
 




<!--HONumber=Nov16_HO1-->


