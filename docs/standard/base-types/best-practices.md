---
title: "正規表現に関するベスト プラクティス"
description: "正規表現に関するベスト プラクティス"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cf9c83de791fa4990a991689a26d4bbdd84cfe7d
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="best-practices-for-regular-expressions"></a><span data-ttu-id="57e21-104">正規表現に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="57e21-104">Best practices for regular expressions</span></span>

<span data-ttu-id="57e21-105">.NET の正規表現エンジンは、リテラル テキストの比較と照合ではなくパターン一致に基づいてテキストを処理する、完全な機能を備えた強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="57e21-105">The regular expression engine in .NET is a powerful, full-featured tool that processes text based on pattern matches rather than on comparing and matching literal text.</span></span> <span data-ttu-id="57e21-106">ほとんどの場合は、すばやく効率的にパターン一致が実行されますが、</span><span class="sxs-lookup"><span data-stu-id="57e21-106">In most cases, it performs pattern matching rapidly and efficiently.</span></span> <span data-ttu-id="57e21-107">処理が非常に遅く見えることもあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-107">However, in some cases, the regular expression engine can appear to be very slow.</span></span> <span data-ttu-id="57e21-108">極端なケースでは、比較的小さな入力の処理に何時間も何日もかかり、応答しなくなったように見えることさえあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-108">In extreme cases, it can even appear to stop responding as it processes a relatively small input over the course of hours or even days.</span></span> 

<span data-ttu-id="57e21-109">ここでは、正規表現で最適なパフォーマンスを確保するためのいくつかのベスト プラクティスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="57e21-109">This topic outlines some of the best practices that developers can adopt to ensure that their regular expressions achieve optimal performance.</span></span> <span data-ttu-id="57e21-110">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="57e21-110">It contains the following sections:</span></span>

* [<span data-ttu-id="57e21-111">入力ソースを考慮に入れる</span><span class="sxs-lookup"><span data-stu-id="57e21-111">Consider the input source</span></span>](#consider-the-input-source)

* [<span data-ttu-id="57e21-112">オブジェクトのインスタンス化を適切に処理する</span><span class="sxs-lookup"><span data-stu-id="57e21-112">Handle object instantiation appropriately</span></span>](#handle-object-instantiation-appropriately)

* [<span data-ttu-id="57e21-113">バックトラッキングを管理する</span><span class="sxs-lookup"><span data-stu-id="57e21-113">Take charge of backtracking</span></span>](#take-charge-of-backtracking)

* [<span data-ttu-id="57e21-114">タイムアウト値を使用する</span><span class="sxs-lookup"><span data-stu-id="57e21-114">Use time-out values</span></span>](#use-time-out-values)

* [<span data-ttu-id="57e21-115">必要なときにのみキャプチャする</span><span class="sxs-lookup"><span data-stu-id="57e21-115">Capture only when necessary</span></span>](#capture-only-when-necessary)

* [<span data-ttu-id="57e21-116">関連トピック</span><span class="sxs-lookup"><span data-stu-id="57e21-116">Related topics</span></span>](#related-topics)

## <a name="consider-the-input-source"></a><span data-ttu-id="57e21-117">入力ソースを考慮に入れる</span><span class="sxs-lookup"><span data-stu-id="57e21-117">Consider the input source</span></span>

<span data-ttu-id="57e21-118">一般に、正規表現で受け入れられる入力には、制約のある入力と制約のない入力の&2; 種類があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-118">In general, regular expressions can accept two types of input: constrained or unconstrained.</span></span> <span data-ttu-id="57e21-119">制約のある入力とは、あらかじめ定義された形式に従っている、既知のソースまたは信頼できるソースからのテキストです。</span><span class="sxs-lookup"><span data-stu-id="57e21-119">Constrained input is text that originates from a known or reliable source and follows a predefined format.</span></span> <span data-ttu-id="57e21-120">制約のない入力とは、あらかじめ定義された形式や予想される形式に従っていない可能性のある、不確実なソース (Web ユーザーなど) からのテキストです。</span><span class="sxs-lookup"><span data-stu-id="57e21-120">Unconstrained input is text that originates from an unreliable source, such as a web user, and may not follow a predefined or expected format.</span></span>

<span data-ttu-id="57e21-121">正規表現パターンは、有効な入力に一致するように記述されるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="57e21-121">Regular expression patterns are typically written to match valid input.</span></span> <span data-ttu-id="57e21-122">開発者はまず、対象となるテキストを調査して、そのテキストに一致する正規表現パターンを記述します。</span><span class="sxs-lookup"><span data-stu-id="57e21-122">That is, developers examine the text that they want to match and then write a regular expression pattern that matches it.</span></span> <span data-ttu-id="57e21-123">記述が完了すると、そのパターンを複数の有効な入力項目でテストして、修正や改善が必要かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-123">Developers then determine whether this pattern requires correction or further elaboration by testing it with multiple valid input items.</span></span> <span data-ttu-id="57e21-124">想定されるすべての有効な入力に一致するようになったら、そのパターンは運用環境で使用する準備が整ったと見なされ、リリースされるアプリケーションに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-124">When the pattern matches all presumed valid inputs, it is declared to be production-ready and can be included in a released application.</span></span> <span data-ttu-id="57e21-125">こうして作成された正規表現パターンは、制約のある入力との照合には適していますが、</span><span class="sxs-lookup"><span data-stu-id="57e21-125">This makes a regular expression pattern suitable for matching constrained input.</span></span> <span data-ttu-id="57e21-126">制約のない入力との照合に適しているとは言えません。</span><span class="sxs-lookup"><span data-stu-id="57e21-126">However, it does not make it suitable for matching unconstrained input.</span></span>

<span data-ttu-id="57e21-127">制約のない入力と照合する正規表現は、次の&3; 種類のテキストを効率的に処理できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="57e21-127">To match unconstrained input, a regular expression must be able to efficiently handle three kinds of text:</span></span>

<span data-ttu-id="57e21-128">• 正規表現パターンに一致するテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e21-128">• Text that matches the regular expression pattern.</span></span>

<span data-ttu-id="57e21-129">• 正規表現パターンに一致しないテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e21-129">• Text that does not match the regular expression pattern.</span></span>

<span data-ttu-id="57e21-130">• 正規表現パターンにほぼ一致するテキスト。</span><span class="sxs-lookup"><span data-stu-id="57e21-130">• Text that nearly matches the regular expression pattern.</span></span>

<span data-ttu-id="57e21-131">制約のある入力を処理するために記述された正規表現で特に問題となるのは、最後の種類のテキストです。</span><span class="sxs-lookup"><span data-stu-id="57e21-131">The last text type is especially problematic for a regular expression that has been written to handle constrained input.</span></span> <span data-ttu-id="57e21-132">その正規表現が広範な[バックトラッキング](backtracking.md)にも依存している場合、一見何の問題もないように見えるテキストの処理に極端に長い時間 (場合によっては何時間も何日も) が費やされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-132">If that regular expression also relies on extensive [backtracking](backtracking.md), the regular expression engine can spend an inordinate amount of time (in some cases, many hours or days) processing seemingly innocuous text.</span></span> 

> [!WARNING]
> <span data-ttu-id="57e21-133">次の例では、過度なバックトラッキングを生じる傾向があり、有効な電子メール アドレスを拒否する可能性がある正規表現を使用します。</span><span class="sxs-lookup"><span data-stu-id="57e21-133">The following example uses a regular expression that is prone to excessive backtracking and that is likely to reject valid email addresses.</span></span> <span data-ttu-id="57e21-134">電子メールの検証ルーチンで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="57e21-134">You should not use it in an email validation routine.</span></span> <span data-ttu-id="57e21-135">メール アドレスを検証する正規表現が必要な場合は、「[方法: 文字列が有効な電子メール形式であるかどうかを検証する](verify-format.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-135">If you would like a regular expression that validates email addresses, see [How to: Verify that strings are in valid email format](verify-format.md).</span></span> 


<span data-ttu-id="57e21-136">例として、電子メール アドレスのエイリアスを検証するための正規表現について見てみましょう。このような正規表現はよく使用されますが、きわめて大きな問題もはらんでいます。</span><span class="sxs-lookup"><span data-stu-id="57e21-136">For example, consider a very commonly used but extremely problematic regular expression for validating the alias of an email address.</span></span> <span data-ttu-id="57e21-137">有効と見なされる電子メール アドレスを処理するために、`^[0-9A-Z]([-.\w]*[0-9A-Z])*$` という正規表現を記述したとします。有効な電子メール アドレスは、英数字で始まり、その後に&0; 個以上の文字 (英数字、ピリオド、またはハイフン) が続きます。</span><span class="sxs-lookup"><span data-stu-id="57e21-137">The regular expression `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` is written to process what is considered to be a valid email address, which consists of an alphanumeric character, followed by zero or more characters that can be alphanumeric, periods, or hyphens.</span></span> <span data-ttu-id="57e21-138">また、正規表現は英数字で終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-138">The regular expression must end with an alphanumeric character.</span></span> <span data-ttu-id="57e21-139">この正規表現は、次の例に示すように、有効な入力は簡単に処理できますが、有効に近い入力を処理するときに極端に処理効率が低下します。</span><span class="sxs-lookup"><span data-stu-id="57e21-139">However, as the following example shows, although this regular expression handles valid input easily, its performance is very inefficient when it is processing nearly valid input.</span></span>

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

<span data-ttu-id="57e21-140">この出力を見るとわかるように、有効な電子メール エイリアスは、その長さに関係なくほとんど同じ時間で処理されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-140">As the output from the example shows, the regular expression engine processes the valid email alias in about the same time interval regardless of its length.</span></span> <span data-ttu-id="57e21-141">一方、有効に近い電子メール アドレスでは、長さが&5; 文字を超えると、文字列の文字が&1; 文字増えるたびに処理時間が約&2; 倍に増加します。</span><span class="sxs-lookup"><span data-stu-id="57e21-141">On the other hand, when the nearly valid email address has more than five characters, processing time approximately doubles for each additional character in the string.</span></span> <span data-ttu-id="57e21-142">つまり、有効に近い文字列の長さが 28 文字になると処理に 1 時間以上かかり、33 文字になるとほぼ 1 日かかることになります。</span><span class="sxs-lookup"><span data-stu-id="57e21-142">This means that a nearly valid 28-character string would take over an hour to process, and a nearly valid 33-character string would take nearly a day to process.</span></span> 

<span data-ttu-id="57e21-143">この正規表現は、一致する入力の形式ばかりを念頭に置いて開発されていて、パターンに一致しない入力のことが考慮されていません。</span><span class="sxs-lookup"><span data-stu-id="57e21-143">Because this regular expression was developed solely by considering the format of input to be matched, it fails to take account of input that does not match the pattern.</span></span> <span data-ttu-id="57e21-144">そのため、制約のない入力が正規表現パターンにほぼ一致する場合に、パフォーマンスが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-144">This, in turn, can allow unconstrained input that nearly matches the regular expression pattern to significantly degrade performance.</span></span>

<span data-ttu-id="57e21-145">この問題を解決する方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="57e21-145">To solve this problem, you can do the following:</span></span>

* <span data-ttu-id="57e21-146">パターンを開発するときには、バックトラッキングが正規表現エンジンのパフォーマンスに与える影響を考慮に入れます。特に、制約のない入力を処理する正規表現ではこれが重要です。</span><span class="sxs-lookup"><span data-stu-id="57e21-146">When developing a pattern, you should consider how backtracking might affect the performance of the regular expression engine, particularly if your regular expression is designed to process unconstrained input.</span></span> <span data-ttu-id="57e21-147">詳細については、このトピックの「[バックトラッキングを管理する](#take-charge-of-backtracking)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-147">For more information, see the [Take charge of backtracking](#take-charge-of-backtracking) section.</span></span>

* <span data-ttu-id="57e21-148">有効な入力だけでなく、無効な入力と有効に近い入力も使用して、正規表現を徹底的にテストします。</span><span class="sxs-lookup"><span data-stu-id="57e21-148">Thoroughly test your regular expression using invalid and near-valid input as well as valid input.</span></span> <span data-ttu-id="57e21-149">特定の正規表現に対する入力をランダムに生成するには、Microsoft Research の正規表現調査ツール [Rex](http://research.microsoft.com/en-us/projects/rex/) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="57e21-149">To generate input for a particular regular expression randomly, you can use [Rex](http://research.microsoft.com/en-us/projects/rex/), which is a regular expression exploration tool from Microsoft Research.</span></span>

## <a name="handle-object-instantiation-appropriately"></a><span data-ttu-id="57e21-150">オブジェクトのインスタンス化を適切に処理する</span><span class="sxs-lookup"><span data-stu-id="57e21-150">Handle object instantiation appropriately</span></span>

<span data-ttu-id="57e21-151">.NET の正規表現オブジェクト モデルの中核となるのは、正規表現エンジンを表す [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) クラスです。</span><span class="sxs-lookup"><span data-stu-id="57e21-151">At the heart of .NET’s regular expression object model is the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) class, which represents the regular expression engine.</span></span> <span data-ttu-id="57e21-152">[Regex](xref:System.Text.RegularExpressions.Regex) エンジンの使用方法は、多くの場合、正規表現のパフォーマンスを左右する最大の要因になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-152">Often, the single greatest factor that affects regular expression performance is the way in which the [Regex](xref:System.Text.RegularExpressions.Regex) engine is used.</span></span> <span data-ttu-id="57e21-153">正規表現を定義するときには、正規表現エンジンと正規表現パターンを密に結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-153">Defining a regular expression involves tightly coupling the regular expression engine with a regular expression pattern.</span></span> <span data-ttu-id="57e21-154">この結合のプロセスは、正規表現パターンをコンストラクターに渡して [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化する場合も、分析する文字列と共に正規表現パターンを渡して静的メソッドを呼び出す場合も、必然的にコストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-154">That coupling process, whether it involves instantiating a [Regex](xref:System.Text.RegularExpressions.Regex) object by passing its constructor a regular expression pattern or calling a static method by passing it the regular expression pattern along with the string to be analyzed, is by necessity an expensive one.</span></span>

<span data-ttu-id="57e21-155">正規表現エンジンを特定の正規表現パターンと結合し、そのエンジンを使用してテキストを照合するには、次のようにいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-155">You can couple the regular expression engine with a particular regular expression pattern and then use the engine to match text in several ways:</span></span>

* <span data-ttu-id="57e21-156">パターン一致を実行する静的メソッド [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) などを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57e21-156">You can call a static pattern-matching method, such as [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span></span> <span data-ttu-id="57e21-157">この場合は、正規表現オブジェクトをインスタンス化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="57e21-157">This does not require instantiation of a regular expression object.</span></span>

* <span data-ttu-id="57e21-158">[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化し、解釈される正規表現のパターン一致を実行するインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57e21-158">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of an interpreted regular expression.</span></span> <span data-ttu-id="57e21-159">これは、正規表現エンジンを正規表現パターンにバインドするための既定の方法です。</span><span class="sxs-lookup"><span data-stu-id="57e21-159">This is the default method for binding the regular expression engine to a regular expression pattern.</span></span> <span data-ttu-id="57e21-160">[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) フラグを含むオプション引数を使用せずに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトがインスタンス化された場合にこのようになります。</span><span class="sxs-lookup"><span data-stu-id="57e21-160">It results when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated without an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

* <span data-ttu-id="57e21-161">[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化し、コンパイルされた正規表現のパターン一致を実行するインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57e21-161">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of a compiled regular expression.</span></span> <span data-ttu-id="57e21-162">[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化するときに、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) フラグを含むオプション引数を指定した場合、正規表現オブジェクトはコンパイル済みのパターンを表します。</span><span class="sxs-lookup"><span data-stu-id="57e21-162">Regular expression objects represent compiled patterns when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated with an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57e21-163">メソッド呼び出しの形式 (静的、解釈、コンパイル) は、メソッド呼び出しで同じ正規表現が繰り返し使用される場合や、アプリケーションで正規表現オブジェクトが多用される場合に、パフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="57e21-163">The form of the method call (static, interpreted, compiled) affects performance if the same regular expression is used repeatedly in method calls, or if an application makes extensive use of regular expression objects.</span></span>
 
### <a name="static-regular-expressions"></a><span data-ttu-id="57e21-164">静的正規表現</span><span class="sxs-lookup"><span data-stu-id="57e21-164">Static regular expressions</span></span>

<span data-ttu-id="57e21-165">静的正規表現メソッドは、正規表現オブジェクトを同じ正規表現で繰り返しインスタンス化する代わりの方法として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-165">Static regular expression methods are recommended as an alternative to repeatedly instantiating a regular expression object with the same regular expression.</span></span> <span data-ttu-id="57e21-166">正規表現オブジェクトで使用される正規表現パターンとは異なり、インスタンス メソッドの呼び出しで使用されるパターンの場合は、そのオペレーション コードまたはコンパイルされた Microsoft Intermediate Language (MSIL) が正規表現エンジンによって内部にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="57e21-166">Unlike regular expression patterns used by regular expression objects, either the operation codes or the compiled Microsoft intermediate language (MSIL) from patterns used in instance method calls is cached internally by the regular expression engine.</span></span> 

<span data-ttu-id="57e21-167">たとえば、ユーザー入力を検証するメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-167">For example, you might call a method to validate user input.</span></span> <span data-ttu-id="57e21-168">この例では `IsValidCurrency` という名前のメソッドが、ユーザーが少なくとも&1; つの&10; 進数を通貨記号の後に入力したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-168">In this example, a method named `IsValidCurrency` checks whether the user has entered a currency symbol followed by at least one decimal digit.</span></span> <span data-ttu-id="57e21-169">次の例は、`IsValidCurrency` メソッドのきわめて非効率的な実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-169">A very inefficient implementation of the `IsValidCurrency` method is shown in the following example.</span></span> <span data-ttu-id="57e21-170">この例では、このメソッドが呼び出されるたびに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトが同じパターンでインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-170">Note that each method call reinstantiates a [Regex](xref:System.Text.RegularExpressions.Regex) object with the same pattern.</span></span> <span data-ttu-id="57e21-171">そのため、メソッドが呼び出されるたびに正規表現パターンを再コンパイルしなければならなくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-171">This, in turn, means that the regular expression pattern must be recompiled each time the method is called.</span></span>

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

<span data-ttu-id="57e21-172">この非効率的なコードは、静的な [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) メソッドの呼び出しに置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-172">You should replace this inefficient code with a call to the static [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) method.</span></span> <span data-ttu-id="57e21-173">これにより、パターン一致メソッドを呼び出すたびに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化する必要がなくなり、正規表現エンジンがキャッシュからコンパイル済みの正規表現を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="57e21-173">This eliminates the need to instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object each time you want to call a pattern-matching method, and enables the regular expression engine to retrieve a compiled version of the regular expression from its cache.</span></span>

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

<span data-ttu-id="57e21-174">既定では、最近使用された静的正規表現パターンが 15 個までキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="57e21-174">By default, the last 15 most recently used static regular expression patterns are cached.</span></span> <span data-ttu-id="57e21-175">アプリケーションで多数の静的正規表現をキャッシュする必要がある場合は、[Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) プロパティを設定してキャッシュのサイズを調整できます。</span><span class="sxs-lookup"><span data-stu-id="57e21-175">For applications that require a larger number of cached static regular expressions, the size of the cache can be adjusted by setting the [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) property.</span></span>

<span data-ttu-id="57e21-176">この例で使用されている正規表現 `\p{Sc}+\s*\d+` は、入力文字列が通貨記号と&1; 文字以上の&10; 進数の数字で構成されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-176">The regular expression `\p{Sc}+\s*\d+` that is used in this example verifies that the input string consists of a currency symbol and at least one decimal digit.</span></span> <span data-ttu-id="57e21-177">このパターンは、次の表に示すように定義されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-177">The pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="57e21-178">パターン</span><span class="sxs-lookup"><span data-stu-id="57e21-178">Pattern</span></span> | <span data-ttu-id="57e21-179">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-179">Description</span></span>
------- | -----------
`\p{Sc}+` | <span data-ttu-id="57e21-180">Unicode の Symbol, Currency カテゴリの&1; 個以上の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-180">Match one or more characters in the Unicode Symbol, Currency category.</span></span>
`\s*` | <span data-ttu-id="57e21-181">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-181">Match zero or more white-space characters.</span></span>
`\d+` | <span data-ttu-id="57e21-182">1 個以上の&10; 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-182">Match one or more decimal digits.</span></span>
 
### <a name="interpreted-vs-compiled-regular-expressions"></a><span data-ttu-id="57e21-183">解釈される正規表現とコンパイルされる正規表現</span><span class="sxs-lookup"><span data-stu-id="57e21-183">Interpreted vs. compiled regular expressions</span></span>

<span data-ttu-id="57e21-184">[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを指定して正規表現エンジンにバインドされていない正規表現パターンは、解釈されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-184">Regular expression patterns that are not bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are interpreted.</span></span> <span data-ttu-id="57e21-185">正規表現オブジェクトがインスタンス化されるとき、正規表現エンジンは、その正規表現を一連のオペレーション コードに変換します。</span><span class="sxs-lookup"><span data-stu-id="57e21-185">When a regular expression object is instantiated, the regular expression engine converts the regular expression to a set of operation codes.</span></span> <span data-ttu-id="57e21-186">インスタンス メソッドが呼び出されると、オペレーション コードが MSIL に変換され、JIT コンパイラによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-186">When an instance method is called, the operation codes are converted to MSIL and executed by the JIT compiler.</span></span> <span data-ttu-id="57e21-187">同様に、静的正規表現メソッドが呼び出され、その正規表現がキャッシュに見つからない場合、正規表現エンジンは、その正規表現を一連のオペレーション コードに変換し、キャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="57e21-187">Similarly, when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to a set of operation codes and stores them in the cache.</span></span> <span data-ttu-id="57e21-188">それらのオペレーション コードは、その後、JIT コンパイラで実行できるように MSIL に変換されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-188">It then converts these operation codes to MSIL so that the JIT compiler can execute them.</span></span> <span data-ttu-id="57e21-189">解釈される正規表現では、実行時間が長くなる代わりに、スタートアップ時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-189">Interpreted regular expressions reduce startup time at the cost of slower execution time.</span></span> <span data-ttu-id="57e21-190">このため、正規表現を使用するメソッドの呼び出し回数が少ない場合、または正確な回数はわからなくても少ないと予想される場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-190">Because of this, they are best used when the regular expression is used in a small number of method calls, or if the exact number of calls to regular expression methods is unknown but is expected to be small.</span></span> <span data-ttu-id="57e21-191">メソッド呼び出しの回数が増えるにつれて、スタートアップ時間の短縮というメリットよりも、実行速度の低下というデメリットの方が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-191">As the number of method calls increases, the performance gain from reduced startup time is outstripped by the slower execution speed.</span></span>

<span data-ttu-id="57e21-192">[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを指定して正規表現エンジンにバインドされている正規表現パターンは、コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="57e21-192">Regular expression patterns that are bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are compiled.</span></span> <span data-ttu-id="57e21-193">つまり、正規表現オブジェクトがインスタンス化されるとき、または静的正規表現メソッドが呼び出され、その正規表現がキャッシュに見つからないとき、正規表現エンジンは、その正規表現を一連の中間的なオペレーション コードに変換し、さらに MSIL に変換します。</span><span class="sxs-lookup"><span data-stu-id="57e21-193">This means that, when a regular expression object is instantiated, or when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to an intermediary set of operation codes, which it then converts to MSIL.</span></span> <span data-ttu-id="57e21-194">メソッドが呼び出されると、その MSIL が JIT コンパイラによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-194">When a method is called, the JIT compiler executes the MSIL.</span></span> <span data-ttu-id="57e21-195">コンパイルされる正規表現では、解釈される正規表現とは対照的に、スタートアップ時間が長くなる一方で、個々のパターン一致メソッドの実行時間は短くなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-195">In contrast to interpreted regular expressions, compiled regular expressions increase startup time but execute individual pattern-matching methods faster.</span></span> <span data-ttu-id="57e21-196">結果として、正規表現のコンパイルによって得られるパフォーマンス上のメリットは、正規表現メソッドが呼び出される回数に比例して大きくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-196">As a result, the performance benefit that results from compiling the regular expression increases in proportion to the number of regular expression methods called.</span></span>

<span data-ttu-id="57e21-197">要約すると、特定の正規表現について正規表現メソッドを呼び出す回数が比較的少ない場合は、解釈される正規表現を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="57e21-197">To summarize, we recommend that you use interpreted regular expressions when you call regular expression methods with a specific regular expression relatively infrequently.</span></span> <span data-ttu-id="57e21-198">特定の正規表現について正規表現メソッドを呼び出す回数が比較的多い場合は、コンパイルされる正規表現を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="57e21-198">You should use compiled regular expressions when you call regular expression methods with a specific regular expression relatively frequently.</span></span> <span data-ttu-id="57e21-199">解釈される正規表現で実行速度の低下がスタートアップ時間の短縮を上回るしきい値や、コンパイルされる正規表現でスタートアップ時間の増加が実行速度の向上を上回るしきい値については、正確な値を特定するのは困難です。</span><span class="sxs-lookup"><span data-stu-id="57e21-199">The exact threshold at which the slower execution speeds of interpreted regular expressions outweigh gains from their reduced startup time, or the threshold at which the slower startup times of compiled regular expressions outweigh gains from their faster execution speeds, is difficult to determine.</span></span> <span data-ttu-id="57e21-200">これは、正規表現の複雑さや、処理される個々のデータなど、さまざまな要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="57e21-200">It depends on a variety of factors, including the complexity of the regular expression and the specific data that it processes.</span></span> <span data-ttu-id="57e21-201">特定のアプリケーションのシナリオにおいて、解釈される正規表現とコンパイルされる正規表現のどちらで最適なパフォーマンスが得られるかを特定するには、[Stopwatch](xref:System.Diagnostics.Stopwatch) クラスを使用して実行時間を比較します。</span><span class="sxs-lookup"><span data-stu-id="57e21-201">To determine whether interpreted or compiled regular expressions offer the best performance for your particular application scenario, you can use the [Stopwatch](xref:System.Diagnostics.Stopwatch) class to compare their execution times.</span></span>

<span data-ttu-id="57e21-202">次の例では、Theodore Dreiser の『The Financier』の最初の&10; 個の文を読み取る場合とすべての文を読み取る場合について、コンパイルされる正規表現と解釈される正規表現のパフォーマンスを比較しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-202">The following example compares the performance of compiled and interpreted regular expressions when reading the first ten sentences and when reading all the sentences in the text of Theodore Dreiser's The Financier.</span></span> <span data-ttu-id="57e21-203">出力を見るとわかるように、正規表現の一致メソッドの呼び出しが&10; 回だけの場合は、解釈される正規表現の方がコンパイルされる正規表現よりパフォーマンスが高くなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-203">As the output from the example shows, when only ten calls are made to regular expression matching methods, an interpreted regular expression offers better performance than a compiled regular expression.</span></span> <span data-ttu-id="57e21-204">しかし、多数の呼び出し (この場合は 13,000 回以上) が行われる場合は、コンパイルされる正規表現の方がパフォーマンスが高くなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-204">However, a compiled regular expression offers better performance when a large number of calls (in this case, over 13,000) are made.</span></span> 

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

<span data-ttu-id="57e21-205">この例で使用する正規表現パターン `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="57e21-205">The regular expression pattern used in the example, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, is defined as shown in the following table.</span></span>

<span data-ttu-id="57e21-206">パターン</span><span class="sxs-lookup"><span data-stu-id="57e21-206">Pattern</span></span> | <span data-ttu-id="57e21-207">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-207">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="57e21-208">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="57e21-208">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="57e21-209">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-209">Match one or more word characters.</span></span>
<span data-ttu-id="57e21-210">\`(\r?\n)</span><span class="sxs-lookup"><span data-stu-id="57e21-210">\`(\r?\n)</span></span>|<span data-ttu-id="57e21-211">,?\s)\`</span><span class="sxs-lookup"><span data-stu-id="57e21-211">,?\s)\`</span></span> | <span data-ttu-id="57e21-212">0 ～&1; 個の復帰とそれに続く改行文字、または&0; ～&1; 個のコンマとそれに続く空白文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-212">Match either zero or one carriage return followed by a newline character, or zero or one comma followed by a white-space character.</span></span>
<span data-ttu-id="57e21-213">\`(\w+((\r?\n)</span><span class="sxs-lookup"><span data-stu-id="57e21-213">\`(\w+((\r?\n)</span></span>|<span data-ttu-id="57e21-214">,?\s))*\`</span><span class="sxs-lookup"><span data-stu-id="57e21-214">,?\s))*\`</span></span> | <span data-ttu-id="57e21-215">1 個以上の単語文字の後に&0; ～&1; 個の復帰と改行文字または&0; ～&1; 個のコンマと空白文字が続くパターンの&0; 回以上の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-215">Match zero or more occurrences of one or more word characters that are followed either by zero or one carriage return and a newline character, or by zero or one comma followed by a white-space character.</span></span>
`\w+` | <span data-ttu-id="57e21-216">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-216">Match one or more word characters.</span></span>
`[.?:;!]` | <span data-ttu-id="57e21-217">ピリオド、疑問符、コロン、セミコロン、または感嘆符に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-217">Match a period, question mark, colon, semicolon, or exclamation point.</span></span>
 
## <a name="take-charge-of-backtracking"></a><span data-ttu-id="57e21-218">バックトラッキングを管理する</span><span class="sxs-lookup"><span data-stu-id="57e21-218">Take charge of backtracking</span></span>

<span data-ttu-id="57e21-219">通常、正規表現エンジンは入力文字列内を直線的に進んで、入力文字列を正規表現パターンと比較します。</span><span class="sxs-lookup"><span data-stu-id="57e21-219">Ordinarily, the regular expression engine uses linear progression to move through an input string and compare it to a regular expression pattern.</span></span> <span data-ttu-id="57e21-220">しかし、正規表現パターン内で不定量指定子 (__*__、**+**、**?** など) </span><span class="sxs-lookup"><span data-stu-id="57e21-220">However, when indeterminate quantifiers such as __*__, **+**, and **?**</span></span> <span data-ttu-id="57e21-221">が使用されていると、パターン全体に対する一致を検索するために、それまでに見つかった部分的な一致を放棄して、以前に保存した状態に戻る場合があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-221">are used in a regular expression pattern, the regular expression engine may give up a portion of successful partial matches and return to a previously saved state in order to search for a successful match for the entire pattern.</span></span> <span data-ttu-id="57e21-222">このプロセスをバックトラッキングと呼びます。</span><span class="sxs-lookup"><span data-stu-id="57e21-222">This process is known as backtracking.</span></span>

> [!NOTE]
> <span data-ttu-id="57e21-223">バックトラッキングの詳細については、「[正規表現の動作の詳細](regex-behavior.md)」と「[正規表現におけるバックトラッキング](backtracking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-223">For more information on backtracking, see [Details of regular expression behavior](regex-behavior.md) and [Backtracking in regular expressions](backtracking.md).</span></span>
 
<span data-ttu-id="57e21-224">バックトラッキングのサポートにより、正規表現はより強力かつ柔軟になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-224">Support for backtracking gives regular expressions power and flexibility.</span></span> <span data-ttu-id="57e21-225">同時に、正規表現エンジンの動作を正規表現の開発者が制御することにもなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-225">It also places the responsibility for controlling the operation of the regular expression engine in the hands of regular expression developers.</span></span> <span data-ttu-id="57e21-226">この責任を認識していない開発者によるバックトラッキングの誤用や過度なバックトラッキングへの依存が、多くの場合、正規表現のパフォーマンスを低下させる最大の要因になっています。</span><span class="sxs-lookup"><span data-stu-id="57e21-226">Because developers are often not aware of this responsibility, their misuse of backtracking or reliance on excessive backtracking often plays the most significant role in degrading regular expression performance.</span></span> <span data-ttu-id="57e21-227">最悪のシナリオでは、入力文字列が&1; 文字増えるたびに実行時間が倍増することもあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-227">In a worst-case scenario, execution time can double for each additional character in the input string.</span></span> <span data-ttu-id="57e21-228">実際、バックトラッキングを過度に使用すると、入力が正規表現パターンにほぼ一致する場合に、プログラム的に無限ループと同等の状態に陥りやすくなります。そのような状態では、正規表現エンジンによる比較的短い入力文字列の処理に何時間も何日もかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-228">In fact, by using backtracking excessively, it is easy to create the programmatic equivalent of an endless loop if input nearly matches the regular expression pattern; the regular expression engine may take hours or even days to process a relatively short input string.</span></span>

<span data-ttu-id="57e21-229">照合に必要でないにもかかわらずバックトラッキングを使用した代償として、アプリケーションのパフォーマンスが低下することもよくあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-229">Often, applications pay a performance penalty for using backtracking despite the fact that backtracking is not essential for a match.</span></span> <span data-ttu-id="57e21-230">例として、`\b\p{Lu}\w*\b` という正規表現について見てみましょう。この正規表現は、次の表に示すように、大文字で始まるすべての単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-230">For example, the regular expression `\b\p{Lu}\w*\b` matches all words that begin with an uppercase character, as the following table shows.</span></span>

<span data-ttu-id="57e21-231">パターン</span><span class="sxs-lookup"><span data-stu-id="57e21-231">Pattern</span></span> | <span data-ttu-id="57e21-232">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-232">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="57e21-233">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="57e21-233">Begin the match at a word boundary.</span></span>
`\p{Lu}` | <span data-ttu-id="57e21-234">大文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-234">Match an uppercase character.</span></span>
`\w*` | <span data-ttu-id="57e21-235">0 個以上の単語に使用される文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-235">Match zero or more word characters.</span></span>
`\b` | <span data-ttu-id="57e21-236">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="57e21-236">End the match at a word boundary.</span></span>
 
<span data-ttu-id="57e21-237">ワード境界は単語文字と同じではなく、単語文字のサブセットでもないため、正規表現エンジンが単語文字の照合中にワード境界を越える可能性はありません。</span><span class="sxs-lookup"><span data-stu-id="57e21-237">Because a word boundary is not the same as, or a subset of, a word character, there is no possibility that the regular expression engine will cross a word boundary when matching word characters.</span></span> <span data-ttu-id="57e21-238">したがって、この正規表現では、バックトラッキングが照合の全体的な成功に寄与することはありません。バックトラッキングを使用すると、正規表現エンジンが単語文字の照合に成功するたびに状態を保存しなければならなくなるため、パフォーマンスを低下させるだけです。</span><span class="sxs-lookup"><span data-stu-id="57e21-238">This means that for this regular expression, backtracking can never contribute to the overall success of any match -- it can only degrade performance, because the regular expression engine is forced to save its state for each successful preliminary match of a word character.</span></span>

<span data-ttu-id="57e21-239">バックトラッキングが不要であることがわかった場合は、**(?>**_subexpression_**)** 言語要素を使用して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-239">If you determine that backtracking is not necessary, you can disable it by using the **(?>**_subexpression_**)** language element.</span></span> <span data-ttu-id="57e21-240">次の例では、2 つの正規表現を使用して入力文字列を解析しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-240">The following example parses an input string by using two regular expressions.</span></span> <span data-ttu-id="57e21-241">1 つはバックトラッキングに依存する `\b\p{Lu}\w*\b`、</span><span class="sxs-lookup"><span data-stu-id="57e21-241">The first, `\b\p{Lu}\w*\b`, relies on backtracking.</span></span> <span data-ttu-id="57e21-242">もう&1; つはバックトラッキングを無効にする `\b\p{Lu}(?>\w*)\b` です。</span><span class="sxs-lookup"><span data-stu-id="57e21-242">The second, `\b\p{Lu}(?>\w*)\b`, disables backtracking.</span></span> <span data-ttu-id="57e21-243">出力を見るとわかるように、どちらも結果は同じになります。</span><span class="sxs-lookup"><span data-stu-id="57e21-243">As the output from the example shows, they both produce the same result.</span></span>

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

<span data-ttu-id="57e21-244">正規表現パターンと入力テキストの照合にバックトラッキングが欠かせない場合もよくあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-244">In many cases, backtracking is essential for matching a regular expression pattern to input text.</span></span> <span data-ttu-id="57e21-245">ただし、過度なバックトラッキングが発生すると、極端にパフォーマンスが低下して、アプリケーションが応答しなくなったように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-245">However, excessive backtracking can severely degrade performance and create the impression that an application has stopped responding.</span></span> <span data-ttu-id="57e21-246">この状況が発生するのは、たとえば、量指定子が入れ子になっていて、外側の部分式に一致するテキストが内側の部分式に一致するテキストのサブセットになっている場合です。</span><span class="sxs-lookup"><span data-stu-id="57e21-246">In particular, this happens when quantifiers are nested and the text that matches the outer subexpression is a subset of the text that matches the inner subexpression.</span></span> 

> [!WARNING]
> <span data-ttu-id="57e21-247">過度なバックトラッキングの回避に加えて、タイムアウト機能を使用して、過度なバックトラッキングによって、正規表現のパフォーマンスが極端に低下するのを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-247">In addition to avoiding excessive backtracking, you should use the timeout feature to ensure that excessive backtracking does not severely degrade regular expression performance.</span></span> <span data-ttu-id="57e21-248">詳細については、「[タイムアウト値を使用する](#use-time-out-values)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-248">For more information, see the [Use time-out values](#use-time-out-values) section.</span></span>
 
<span data-ttu-id="57e21-249">例として、部品番号に一致するように作られた `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` という正規表現パターンについて見てみましょう。この部品番号は、少なくとも&1; 文字の英数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-249">For example, the regular expression pattern `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` is intended to match a part number that consists of at least one alphanumeric character.</span></span> <span data-ttu-id="57e21-250">追加の文字では、英数字、ハイフン、アンダースコア、およびピリオドが許容されますが、最後の文字は英数字でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="57e21-250">Any additional characters can consist of an alphanumeric character, a hyphen, an underscore, or a period, though the last character must be alphanumeric.</span></span> <span data-ttu-id="57e21-251">部品番号の終わりはドル記号で示されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-251">A dollar sign terminates the part number.</span></span> <span data-ttu-id="57e21-252">この正規表現パターンは、量指定子が入れ子になっているうえに、部分式 `[0-9A-Z]` が部分式 `[-.\w]*` のサブセットであるため、パフォーマンスが極端に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-252">In some cases, this regular expression pattern can exhibit extremely poor performance because quantifiers are nested, and because the subexpression `[0-9A-Z]` is a subset of the subexpression `[-.\w]*`.</span></span>

<span data-ttu-id="57e21-253">このような場合に正規表現のパフォーマンスを最適化するには、入れ子になった量指定子を削除して、外側の部分式をゼロ幅の先読みアサーションまたは後読みアサーションに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="57e21-253">In these cases, you can optimize regular expression performance by removing the nested quantifiers and replacing the outer subexpression with a zero-width lookahead or lookbehind assertion.</span></span> <span data-ttu-id="57e21-254">先読みアサーションと後読みアサーションはアンカーなので、入力文字列内でポインターを移動させることなく、先読みまたは後読みによって、指定された条件が満たされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-254">Lookahead and lookbehind assertions are anchors; they do not move the pointer in the input string, but instead look ahead or behind to check whether a specified condition is met.</span></span> <span data-ttu-id="57e21-255">たとえば、この部品番号の正規表現は `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$` として書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-255">For example, the part number regular expression can be rewritten as `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span></span> <span data-ttu-id="57e21-256">この正規表現パターンは、次の表に示すように定義されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-256">This regular expression pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="57e21-257">パターン</span><span class="sxs-lookup"><span data-stu-id="57e21-257">Pattern</span></span> | <span data-ttu-id="57e21-258">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-258">Description</span></span>
------- | -----------
`^` | <span data-ttu-id="57e21-259">入力文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="57e21-259">Begin the match at the beginning of the input string.</span></span>
`[0-9A-Z]` | <span data-ttu-id="57e21-260">英数字&1; 文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-260">Match an alphanumeric character.</span></span> <span data-ttu-id="57e21-261">これは、部品番号に最低限必要な文字です。</span><span class="sxs-lookup"><span data-stu-id="57e21-261">The part number must consist of at least this character.</span></span>
`[-.\w]*` | <span data-ttu-id="57e21-262">任意の単語文字、ハイフン、またはピリオドの&0; 回以上の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-262">Match zero or more occurrences of any word character, hyphen, or period.</span></span>
<span data-ttu-id="57e21-263">\`\$]</span><span class="sxs-lookup"><span data-stu-id="57e21-263">\`\$]</span></span> | <span data-ttu-id="57e21-264">ドル記号に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-264">Match a dollar sign.</span></span>
`(?<=[0-9A-Z])` | <span data-ttu-id="57e21-265">末尾のドル記号を先読みし、前の文字が英数字であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-265">Look ahead of the ending dollar sign to ensure that the previous character is alphanumeric.</span></span>
<span data-ttu-id="57e21-266">`$` 入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="57e21-266">`$` End the match at the end of the input string.</span></span>
 
<span data-ttu-id="57e21-267">次の例では、この正規表現を使用して、部品番号を含む配列を照合しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-267">The following example illustrates the use of this regular expression to match an array containing possible part numbers.</span></span>

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

<span data-ttu-id="57e21-268">.NET の正規表現言語には、入れ子になった量指定子を取り除くために使用できる次の言語要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="57e21-268">The regular expression language in .NET includes the following language elements that you can use to eliminate nested quantifiers.</span></span> <span data-ttu-id="57e21-269">詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-269">For more information, see [Grouping constructs in regular expressions](grouping.md).</span></span>

<span data-ttu-id="57e21-270">言語要素</span><span class="sxs-lookup"><span data-stu-id="57e21-270">Language element</span></span> | <span data-ttu-id="57e21-271">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-271">Description</span></span>
---------------- | ----------- 
<span data-ttu-id="57e21-272">**(?**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="57e21-272">**(?**=_subexpression_**)**</span></span> | <span data-ttu-id="57e21-273">ゼロ幅の肯定先読みです。</span><span class="sxs-lookup"><span data-stu-id="57e21-273">Zero-width positive lookahead.</span></span> <span data-ttu-id="57e21-274">現在の位置からの先読みにより、*subexpression* が入力文字列に一致するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-274">Look ahead of the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="57e21-275">**(?!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="57e21-275">**(?!**_subexpression_**)**</span></span> | <span data-ttu-id="57e21-276">ゼロ幅の否定先読みです。</span><span class="sxs-lookup"><span data-stu-id="57e21-276">Zero-width negative lookahead.</span></span> <span data-ttu-id="57e21-277">現在の位置からの先読みにより、*subexpression* が入力文字列に一致しないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-277">Look ahead of the current position to determine whether *subexpression* does not match the input string.</span></span>
<span data-ttu-id="57e21-278">**(?<**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="57e21-278">**(?<**=_subexpression_**)**</span></span> | <span data-ttu-id="57e21-279">ゼロ幅の肯定後読みです。</span><span class="sxs-lookup"><span data-stu-id="57e21-279">Zero-width positive lookbehind.</span></span> <span data-ttu-id="57e21-280">現在の位置からの後読みにより、*subexpression* が入力文字列に一致するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-280">Look behind the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="57e21-281">**(?<!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="57e21-281">**(?<!**_subexpression_**)**</span></span> | <span data-ttu-id="57e21-282">ゼロ幅の否定後読みです。</span><span class="sxs-lookup"><span data-stu-id="57e21-282">Zero-width negative lookbehind.</span></span> <span data-ttu-id="57e21-283">現在の位置からの後読みにより、*subexpression* が入力文字列に一致しないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57e21-283">Look behind the current position to determine whether *subexpression* does not match the input string.</span></span>
 
## <a name="use-time-out-values"></a><span data-ttu-id="57e21-284">タイムアウト値を使用する</span><span class="sxs-lookup"><span data-stu-id="57e21-284">Use time-out values</span></span>

<span data-ttu-id="57e21-285">正規表現が正規表現パターンにほぼ一致する入力を処理する場合は、パフォーマンスに大きな影響を与える過度なバックトラッキングに依存することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-285">If your regular expressions processes input that nearly matches the regular expression pattern, it can often rely on excessive backtracking, which impacts its performance significantly.</span></span> <span data-ttu-id="57e21-286">慎重にバックトラッキングの使用を検討し、ほぼ一致する入力に対して正規表現をテストすることに加えて、過度なバックトラッキングが発生した場合にその影響を確実に最小限に抑えるために、必ずタイムアウト値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-286">In addition to carefully considering your use of backtracking and testing the regular expression against near-matching input, you should always set a time-out value to ensure that the impact of excessive backtracking, if it occurs, is minimized.</span></span>

<span data-ttu-id="57e21-287">正規表現のタイムアウト間隔は、タイムアウトする前に正規表現エンジンが単一の一致を検索する期間を定義します。</span><span class="sxs-lookup"><span data-stu-id="57e21-287">The regular expression time-out interval defines the period of time that the regular expression engine will look for a single match before it times out.</span></span> <span data-ttu-id="57e21-288">既定のタイムアウト間隔は [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout) で、正規表現がタイムアウトしないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="57e21-288">The default time-out interval is [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), which means that the regular expression will not time out.</span></span> <span data-ttu-id="57e21-289">次のようにこの値をオーバーライドし、タイムアウト間隔を定義できます。</span><span class="sxs-lookup"><span data-stu-id="57e21-289">You can override this value and define a time-out interval as follows:</span></span> 

* <span data-ttu-id="57e21-290">[Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) コンストラクターを呼び出すことによって、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化するときに、タイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="57e21-290">By providing a time-out value when you instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object by calling the [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) constructor.</span></span>

* <span data-ttu-id="57e21-291">[Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan))、[Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) など、*matchTimeout* パラメーターを含む静的パターン一致メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57e21-291">By calling a static pattern matching method, such as [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) or [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), that includes a *matchTimeout* parameter.</span></span>

<span data-ttu-id="57e21-292">タイムアウト間隔を定義していて、その間隔の終了時に一致が見つからない場合、正規表現メソッドは [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="57e21-292">If you have defined a time-out interval and a match is not found at the end of that interval, the regular expression method throws a [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) exception.</span></span> <span data-ttu-id="57e21-293">例外ハンドラーで、タイムアウト間隔を延長して一致を再試行する、一致操作を破棄して一致なしと見なす、または一致操作を破棄して今後の分析のために例外情報を記録することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="57e21-293">In your exception handler, you can choose to retry the match with a longer time-out interval, abandon the match attempt and assume that there is no match, or abandon the match attempt and log the exception information for future analysis.</span></span>

<span data-ttu-id="57e21-294">次の例では、テキスト ドキュメントの単語の数と 1 つの単語に含まれる平均文字数を計算するために、タイムアウト間隔が 350 ミリ秒の正規表現をインスタンス化する `GetWordData` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="57e21-294">The following example defines a `GetWordData` method that instantiates a regular expression with a time-out interval of 350 milliseconds to calculate the number of words and average number of characters in a word in a text document.</span></span> <span data-ttu-id="57e21-295">一致操作がタイムアウトした場合、タイムアウト間隔は 350 ミリ秒ずつ延長され、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトが再インスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-295">If the matching operation times out, the time-out interval is increased by 350 milliseconds and the [Regex](xref:System.Text.RegularExpressions.Regex) object is re-instantiated.</span></span> <span data-ttu-id="57e21-296">新しいタイムアウト間隔が 1 秒を超える場合、メソッドは呼び出し元に例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="57e21-296">If the new time-out interval exceeds 1 second, the method re-throws the exception to the caller.</span></span>

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

## <a name="capture-only-when-necessary"></a><span data-ttu-id="57e21-297">必要なときにのみキャプチャする</span><span class="sxs-lookup"><span data-stu-id="57e21-297">Capture only when necessary</span></span>

<span data-ttu-id="57e21-298">.NET の正規表現では、数多くのグループ化構成体がサポートされています。これらを使用すると、正規表現パターンを&1; つ以上の部分式にグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-298">Regular expressions in .NET support a number of grouping constructs, which let you group a regular expression pattern into one or more subexpressions.</span></span> <span data-ttu-id="57e21-299">.NET の正規表現言語で最もよく使用されるグループ化構成体は、番号付きのキャプチャ グループを定義する **(**_subexpression_**)** と、名前付きのキャプチャ グループを定義する **(?<*_name_**>**_subexpression_**)** です。</span><span class="sxs-lookup"><span data-stu-id="57e21-299">The most commonly used grouping constructs in .NET regular expression language are **(**_subexpression_**)**, which defines a numbered capturing group, and **(?<*_name_**>**_subexpression_**)**, which defines a named capturing group.</span></span> <span data-ttu-id="57e21-300">グループ化構成体は、前方参照を作成したり、量指定子を適用する部分式を定義したりするのに欠かせません。</span><span class="sxs-lookup"><span data-stu-id="57e21-300">Grouping constructs are essential for creating backreferences and for defining a subexpression to which a quantifier is applied.</span></span> 

<span data-ttu-id="57e21-301">しかし、これらの言語要素の使用にはコストが伴います。</span><span class="sxs-lookup"><span data-stu-id="57e21-301">However, the use of these language elements has a cost.</span></span> <span data-ttu-id="57e21-302">まず、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティから返される [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトに、最新の名前のないキャプチャまたは名前付きキャプチャが設定されます。また、1 つのグループ化構成体によって入力文字列の複数の部分文字列がキャプチャされた場合は、特定のキャプチャ グループの [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) プロパティから返される [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトに複数の [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトが設定されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-302">They cause the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property to be populated with the most recent unnamed or named captures, and if a single grouping construct has captured multiple substrings in the input string, they also populate the [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) object returned by the [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) property of a particular capturing group with multiple [Capture](xref:System.Text.RegularExpressions.Capture) objects.</span></span>

<span data-ttu-id="57e21-303">正規表現内で量指定子を適用できるようにするためだけにグループ化構成体が使用されていて、それらの部分式によってキャプチャされたグループがその後に使用されていない場合もよくあります。</span><span class="sxs-lookup"><span data-stu-id="57e21-303">Often, grouping constructs are used in a regular expression only so that quantifiers can be applied to them, and the groups captured by these subexpressions are not subsequently used.</span></span> <span data-ttu-id="57e21-304">例として、文全体をキャプチャするために作られた正規表現 `\b(\w+[;,]?\s?)+[.?!]` について見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="57e21-304">For example, the regular expression `\b(\w+[;,]?\s?)+[.?!]` is designed to capture an entire sentence.</span></span> <span data-ttu-id="57e21-305">次の表は、この正規表現パターン内の言語要素と、[Match](xref:System.Text.RegularExpressions.Match) オブジェクトの [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) コレクションおよび [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) コレクションに対する影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="57e21-305">The following table describes the language elements in this regular expression pattern and their effect on the [Match](xref:System.Text.RegularExpressions.Match) object's [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) and [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) collections.</span></span>

<span data-ttu-id="57e21-306">パターン</span><span class="sxs-lookup"><span data-stu-id="57e21-306">Pattern</span></span> | <span data-ttu-id="57e21-307">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-307">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="57e21-308">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="57e21-308">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="57e21-309">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-309">Match one or more word characters.</span></span>
`[;,]?` | <span data-ttu-id="57e21-310">0 個または&1; 個のコンマまたはセミコロンに一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-310">Match zero or one comma or semicolon.</span></span>
`\s?` | <span data-ttu-id="57e21-311">0 個または&1; 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-311">Match zero or one white-space character.</span></span>
`(\w+[;,]?\s?)+` | <span data-ttu-id="57e21-312">1 個以上の単語文字の後に省略可能なコンマまたはセミコロンと省略可能な空白文字が続くパターンの&1; 回以上の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-312">Match one or more occurrences of one or more word characters followed by an optional comma or semicolon followed by an optional white-space character.</span></span> <span data-ttu-id="57e21-313">これにより、最初のキャプチャ グループが定義されます。このグループは、複数の単語文字の組み合わせ (つまり単語) の後に省略可能な区切り記号が続くパターンが、正規表現エンジンが文の終わりに到達するまで繰り返されるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="57e21-313">This defines the first capturing group, which is necessary so that the combination of multiple word characters (that is, a word) followed by an optional punctuation symbol will be repeated until the regular expression engine reaches the end of a sentence.</span></span>
`[.?!]` | <span data-ttu-id="57e21-314">ピリオド、疑問符、または感嘆符に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-314">Match a period, question mark, or exclamation point.</span></span>
 
<span data-ttu-id="57e21-315">次の例に示すように、一致が見つかると、[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトと [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトの両方に一致からのキャプチャが設定されます。</span><span class="sxs-lookup"><span data-stu-id="57e21-315">As the following example shows, when a match is found, both the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) objects are populated with captures from the match.</span></span> <span data-ttu-id="57e21-316">ここでは、**+** 量指定子を適用できるようにするためにキャプチャ グループ `(\w+[;,]?\s?)` が使用されているため、正規表現パターンが文の各単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-316">In this case, the capturing group `(\w+[;,]?\s?)` exists so that the **+** quantifier can be applied to it, which enables the regular expression pattern to match each word in a sentence.</span></span> <span data-ttu-id="57e21-317">そうでない場合は、文の最後の単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="57e21-317">Otherwise, it would match the last word in a sentence.</span></span>

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

<span data-ttu-id="57e21-318">量指定子を適用するためだけに部分式を使用していて、キャプチャされたテキストは特に必要ないという場合は、グループ キャプチャを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-318">When you use subexpressions only to apply quantifiers to them, and you are not interested in the captured text, you should disable group captures.</span></span> <span data-ttu-id="57e21-319">たとえば、**(?:**_subexpression_**)** 言語要素をグループに適用すると、そのグループでは、一致した部分文字列がキャプチャされなくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-319">For example, the **(?:**_subexpression_**)** language element prevents the group to which it applies from capturing matched substrings.</span></span> <span data-ttu-id="57e21-320">次の例では、前の例の正規表現パターンが `\b(?:\w+[;,]?\s?)+[.?!]` に変更されています。</span><span class="sxs-lookup"><span data-stu-id="57e21-320">In the following example, the regular expression pattern from the previous example is changed to `\b(?:\w+[;,]?\s?)+[.?!]`.</span></span> <span data-ttu-id="57e21-321">出力を見るとわかるように、これにより、[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) コレクションと [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) コレクションが設定されなくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-321">As the output shows, it prevents the regular expression engine from populating the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) collections.</span></span>

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

<span data-ttu-id="57e21-322">キャプチャを無効にするには次のような方法があります。</span><span class="sxs-lookup"><span data-stu-id="57e21-322">You can disable captures in one of the following ways:</span></span>

* <span data-ttu-id="57e21-323">**(?:**_subexpression_**)** 言語要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="57e21-323">Use the **(?:**_subexpression_**)** language element.</span></span> <span data-ttu-id="57e21-324">この要素をグループに適用すると、そのグループでは、一致した部分文字列がキャプチャされなくなります。</span><span class="sxs-lookup"><span data-stu-id="57e21-324">This element prevents the capture of matched substrings in the group to which it applies.</span></span> <span data-ttu-id="57e21-325">入れ子になったグループによる部分文字列のキャプチャは無効になりません。</span><span class="sxs-lookup"><span data-stu-id="57e21-325">It does not disable substring captures in any nested groups.</span></span>

* <span data-ttu-id="57e21-326">[RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="57e21-326">Use the [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) option.</span></span> <span data-ttu-id="57e21-327">これにより、正規表現パターン内の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-327">It disables all unnamed or implicit captures in the regular expression pattern.</span></span> <span data-ttu-id="57e21-328">このオプションを使用した場合は、**(?<**_name_**>**_subexpression_**)** 言語要素を使用して定義した名前付きグループに一致する部分文字列のみがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="57e21-328">When you use this option, only substrings that match named groups defined with the **(?<**_name_**>**_subexpression_**)** language element can be captured.</span></span> <span data-ttu-id="57e21-329">[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) フラグは、[Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターの options パラメーターか、[Regex](xref:System.Text.RegularExpressions.Regex) の静的な一致メソッドの options パラメーターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="57e21-329">The [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) flag can be passed to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) class constructor or to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) static matching method.</span></span>

* <span data-ttu-id="57e21-330">**(?imnsx)** 言語要素の **n** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="57e21-330">Use the **n** option in the **(?imnsx)** language element.</span></span> <span data-ttu-id="57e21-331">これにより、正規表現パターンでこの要素が出現する位置以降の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-331">This option disables all unnamed or implicit captures from the point in the regular expression pattern at which the element appears.</span></span> <span data-ttu-id="57e21-332">パターンの末尾に到達するか、**(-n)** オプションによって名前のないキャプチャ (暗黙的なキャプチャ) が有効になるまで、キャプチャは無効のままです。</span><span class="sxs-lookup"><span data-stu-id="57e21-332">Captures are disabled either until the end of the pattern or until the **(-n)** option enables unnamed or implicit captures.</span></span> <span data-ttu-id="57e21-333">詳細については、「[正規表現でのその他の構成体](miscellaneous.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e21-333">For more information, see [Miscellaneous constructs in regular expressions](miscellaneous.md).</span></span>

* <span data-ttu-id="57e21-334">**(?imnsx:**_subexpression_**)** 言語要素の **n** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="57e21-334">Use the **n** option in the **(?imnsx:**_subexpression_**)** language element.</span></span> <span data-ttu-id="57e21-335">これにより、*subexpression* 内の名前のないキャプチャ (暗黙的なキャプチャ) がすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-335">This option disables all unnamed or implicit captures in *subexpression*.</span></span> <span data-ttu-id="57e21-336">入れ子になった名前のない (暗黙的な) キャプチャ グループによるキャプチャも無効になります。</span><span class="sxs-lookup"><span data-stu-id="57e21-336">Captures by any unnamed or implicit nested capturing groups are disabled as well.</span></span>

## <a name="related-topics"></a><span data-ttu-id="57e21-337">関連トピック</span><span class="sxs-lookup"><span data-stu-id="57e21-337">Related topics</span></span>

<span data-ttu-id="57e21-338">タイトル</span><span class="sxs-lookup"><span data-stu-id="57e21-338">Title</span></span> | <span data-ttu-id="57e21-339">説明</span><span class="sxs-lookup"><span data-stu-id="57e21-339">Description</span></span>
----- | ----------- 
[<span data-ttu-id="57e21-340">正規表現の動作の詳細</span><span class="sxs-lookup"><span data-stu-id="57e21-340">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="57e21-341">.NET の正規表現エンジンの実装について検討します。</span><span class="sxs-lookup"><span data-stu-id="57e21-341">Examines the implementation of the regular expression engine in .NET.</span></span> <span data-ttu-id="57e21-342">正規表現の柔軟性に焦点を当てて、正規表現エンジンの効率的かつ堅牢な動作を確保するための開発者の責任について説明します。</span><span class="sxs-lookup"><span data-stu-id="57e21-342">The topic focuses on the flexibility of regular expressions and explains the developer's responsibility for ensuring the efficient and robust operation of the regular expression engine.</span></span>
[<span data-ttu-id="57e21-343">正規表現におけるバックトラッキング</span><span class="sxs-lookup"><span data-stu-id="57e21-343">Backtracking in regular expressions</span></span>](backtracking.md) | <span data-ttu-id="57e21-344">バックトラッキングの概要と、正規表現のパフォーマンスに与える影響について説明し、バックトラッキングの代わりに使用できる言語要素について検討します。</span><span class="sxs-lookup"><span data-stu-id="57e21-344">Explains what backtracking is and how it affects regular expression performance, and examines language elements that provide alternatives to backtracking.</span></span>
[<span data-ttu-id="57e21-345">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="57e21-345">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="57e21-346">.NET の正規表現言語の言語要素について説明します。各言語要素の詳細な説明へのリンクも含まれています。</span><span class="sxs-lookup"><span data-stu-id="57e21-346">Describes the elements of the regular expression language in .NET and provides links to detailed documentation for each language element.</span></span>
 


