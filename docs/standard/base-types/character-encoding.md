---
title: ".NET での文字エンコード"
description: ".NET での文字エンコード"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e72540726bdd1b3624064c7388e58d80320c5831

---

# <a name="character-encoding-in-net"></a>.NET での文字エンコード

文字は、さまざまな方法で表現できる抽象エンティティです。 文字エンコーディングとは、サポートされている文字セットの各文字を、その文字を表す値と組み合わせる体系です。 たとえばモールス符号は、ローマ字の各文字を、電信線での送信に適したドットとダッシュのパターンと組み合わせる文字エンコーディングです。 コンピューターの文字エンコーディングは、サポートされている文字セットの各文字を、その文字を表す数値と組み合わせます。 文字エンコーディングには、次の 2 つの異なるコンポーネントがあります。

* エンコーダー。文字シーケンスを数値 (バイト) シーケンスに変換します。

* デコーダー。バイト シーケンスを文字シーケンスに変換します。

文字エンコーディングは、エンコーダーとデコーダーの動作を決める規則を表します。 たとえば、[UTF8Encoding](xref:System.Text.UTF8Encoding) クラスは、1 ～ 4 バイトを使用して 1 つの Unicode 文字を表現する UTF-8 (8-bit Unicode Transformation Format) をエンコードおよびデコードするための規則を表します。 エンコードとデコードに検証を含めることもできます。 たとえば、[UnicodeEncoding](xref:System.Text.UnicodeEncoding) クラスは、すべてのサロゲートを検証して、有効なサロゲート ペアが構成されていることを確認します  (サロゲート ペアは、U+D800 ～ U+DBFF の範囲のコード ポイントを持つ文字と、それに続く U+DC00 ～ U+DFFF の範囲のコード ポイントを持つ文字で構成されます)。エンコーダーが無効な文字を処理する方法や、デコーダーが無効なバイトを処理する方法は、フォールバック ストラテジによって決まります。 

> [!WARNING]
> .NET のエンコーディング クラスは、文字データを格納および変換するためのものです。 バイナリ データを文字列形式で格納する目的では使用しないでください。 エンコーディング クラスを使用してバイナリ データを文字列形式に変換すると、使用されているエンコーディングによっては、予期しない動作が発生したり、不正確なデータや破損したデータが生成されたりする可能性があります。 バイナリ データを文字列形式に変換するには、[Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) メソッドを使用します。 
 
.NET では ([UnicodeEncoding](xref:System.Text.UnicodeEncoding) クラスによって表される) UTF-16 エンコーディングを使用して、文字と文字列を表します。 共通言語ランタイムをターゲットとするアプリケーションは、エンコーダーを使用して、共通言語ランタイムによってサポートされている Unicode 文字表現を他のエンコーディング方式に変換し、 デコーダーを使用して、Unicode 以外のエンコーディングの文字を Unicode に変換します。

このトピックは、次のセクションで構成されています。

* [.NET でのエンコード](#encodings-in-net)

* [エンコーディング クラスの選択](#selecting-an-encoding-class)

* [エンコーディング オブジェクトの使用](#using-an-encoding-object)

* [フォールバック ストラテジの選択](#choosing-a-fallback-strategy)

* [カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a>.NET でのエンコード

.NET のすべての文字エンコーディング クラスは、すべての文字エンコーディングに共通の機能を定義する抽象クラスの [System.Text.Encoding](xref:System.Text.Encoding) クラスを継承します。 .NET に実装されている個々のエンコーディング オブジェクトにアクセスするには次の方法があります。

* [Encoding](xref:System.Text.Encoding) クラスの静的プロパティを使用します。これらのプロパティは、.NET で使用できる標準の文字エンコーディング (ASCII、UTF-7、UTF-8、UTF-16、および UTF-32) を表すオブジェクトを返します。 たとえば、[Encoding.Unicode](xref:System.Text.Encoding.Unicode) プロパティは [UnicodeEncoding](xref:System.Text.UnicodeEncoding) オブジェクトを返します。 各オブジェクトでは、エンコードできない文字列とデコードできないバイトを処理するために、置換フォールバックが使用されます  (詳細については、「[置換フォールバック](#replacement-fallback)」を参照してください)。

* エンコーディングのクラス コンストラクターを呼び出します。 ASCII、UTF-7、UTF-8、UTF-16、および UTF-32 の各エンコーディングのオブジェクトは、この方法でインスタンス化できます。 既定では、各オブジェクトはエンコードできない文字列とデコードできないバイトを処理するために置換フォールバックを使用します。ただし、代わりに例外がスローされるように指定することもできます  (詳細については、「[置換フォールバック](#replacement-fallback)」と「[例外フォールバック](#exception-fallback)」を参照してください)。

* [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) コンストラクターを呼び出して、エンコーディングを表す整数を渡します。 エンコードできない文字列とデコードできないバイトの処理には、標準エンコーディングのエンコーディング オブジェクトでは置換フォールバックが、コード ページ エンコーディングと 2 バイト文字セット (DBCS) エンコーディングのエンコーディング オブジェクトでは最適フォールバックが使用されます  (詳細については、「[最適フォールバック](#best-fit-fallback)」を参照してください)。

* [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) メソッドを呼び出します。このメソッドは、.NET で使用できる任意のエンコーディング (標準、コード ページ、または DBCS) を返します。 オーバーロードを使用すると、エンコーダーおよびデコーダーの両方のフォールバック オブジェクトを指定できます。

> [!NOTE]
> Unicode 規格では、サポートされるすべてのスクリプトについて、各文字にコード ポイント (数値) と名前を割り当てています。 たとえば、文字 "A" は U+0041 というコード ポイントと、"LATIN CAPITAL LETTER A" という名前で表されます。 UTF (Unicode Transformation Format) エンコーディングは、そのコード ポイントを 1 つ以上のバイトのシーケンスにエンコードする方法を定義します。 Unicode エンコーディング方式を使用すると、任意の文字セットの文字を 1 つのエンコーディング方式で表現できるため、国際対応アプリケーションの開発が簡素化されます。 これにより、アプリケーション開発者が、特定の言語または書記体系の文字を表すために使用されるエンコーディング方式を追跡する必要はなくなります。また、データを破損することなく、各国のシステム間でデータを共有できます。
>
>  .NET では、Unicode 規格によって定義されている UTF-8、UTF-16、および UTF-32 の 3 つのエンコーディングをサポートしています。 詳細については、[Unicode](http://www.unicode.org/) ホーム ページの Unicode 標準を参照してください。
 
.NET でサポートされている文字エンコーディング システムを次の表に示します。

エンコード | クラス | 説明 | 長所/短所
-------- | ----- | ----------- | ------------------------ 
ASCII | [ASCIIEncoding](xref:System.Text.ASCIIEncoding) | バイトの下位 7 ビットを使用して、限られた範囲の文字をエンコードします。 | ASCII エンコーディングでは、U+0000 から U+007F までの文字値しかサポートされていないため、ほとんどの場合、国際対応アプリケーションでは ASCII エンコーディングの使用は不適切です。
UTF-7 | [UTF7Encoding](xref:System.Text.UTF7Encoding) | 文字を 7 ビット ASCII 文字のシーケンスとして表します。 ASCII 以外の Unicode 文字は、ASCII 文字のエスケープ シーケンスによって表します。 | UTF-7 は、電子メールやニュースグループなどのプロトコルをサポートします。 ただし、UTF-7 は特に安全でも堅牢でもありません。 場合によっては、1 ビットの変更により、UTF-7 文字列全体の解釈が完全に変わる場合があります。 他の場合には、異なる UTF-7 文字列がエンコードによって同じテキストになる可能性もあります。 ASCII 以外の文字を含むシーケンスの場合、UTF-7 は UTF-8 よりも多くの空間を必要とし、エンコードとデコードに時間がかかります。 したがって、可能であれば、UTF-7 ではなく UTF-8 を使用してください。
UTF-8 | [UTF8Encoding](xref:System.Text.UTF8Encoding) | 各 Unicode コード ポイントが、1 バイトから 4 バイトのシーケンスとして表現されます。 | UTF-8 では、8 ビット データ サイズがサポートされており、既存の多くのオペレーティング システムに対応できます。 ASCII 範囲の文字については、UTF-8 は ASCII エンコーディングと一致し、より広範な文字を提供します。 ただし、CJK (中国語、日本語、韓国語) スクリプトでは、UTF-8 の各文字に 3 バイトが必要となることがあり、データ サイズが UTF-16 より大きくなる可能性があります。 ただし、CJK 範囲によるサイズの増加が HTML タグなどの ASCII データのサイズによって相殺されることもあります。
UTF-16 | [UnicodeEncoding](xref:System.Text.UnicodeEncoding) | 各 Unicode コード ポイントが、1 つまたは 2 つの 16 ビット整数のシーケンスとして表現されます。 ほとんどの一般的な Unicode 文字で必要とされる UTF-16 コード ポイントは 1 つだけです。ただし、Unicode の補助文字 (U+10000 以上) には 2 つの UTF-16 サロゲート コード ポイントが必要です。 リトル エンディアンとビッグ エンディアンの両方のバイト順をサポートしています。 | UTF-16 エンコーディングは、共通言語ランタイムでは Char および String の値を表現するために、Windows オペレーティング システムでは WCHAR の値を表現するために使用されています。
UTF-32 | [UTF32Encoding](xref:System.Text.UTF32Encoding) | 各 Unicode コード ポイントが 32 ビット整数として表現されます。 リトル エンディアンとビッグ エンディアンの両方のバイト順をサポートしています。 | UTF-32 エンコーディングは、エンコードされた空白がきわめて重要な意味を持つオペレーティング システムで、アプリケーションが UTF-16 エンコーディングのサロゲート コード ポイント動作を回避する必要がある場合に使用します。 ディスプレイ上でレンダリングされる 1 つのグリフも複数の UTF-32 文字でエンコードされることがあります。

これらのエンコーディングを使用することにより、Unicode 文字だけでなく、レガシ アプリケーションで最もよく使用されているエンコーディングにも対応できます。 また、[Encoding](xref:System.Text.Encoding) から派生するクラスを定義し、そのメンバーをオーバーライドして、カスタム エンコーディングを作成することもできます。

> [!NOTE]
> 既定で、.NET Core では、コード ページ 28591 以外のコード ページ エンコーディングや Unicode エンコーディング (UTF-8 や UTF-16 など) を使用できません。 ただし、使用するアプリに、.NET Framework を対象とする標準の Windows アプリに含まれているコード ページ エンコーディングを追加できます。 詳細については、「[EncodingProvider](xref:System.Text.EncodingProvider)」のトピックを参照してください。 

## <a name="selecting-an-encoding-class"></a>エンコーディング クラスの選択

アプリケーションで使用するエンコーディングを選択できる場合は、Unicode エンコーディング (できれば [UTF8Encoding](xref:System.Text.UTF8Encoding) または [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) を使用するようにしてください  (.NET でサポートされている Unicode エンコーディングには、そのほかに [UTF32Encoding](xref:System.Text.UTF32Encoding) もあります)。 

ASCII エンコーディング ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)) を使用しようとしている場合は、代わりに [UTF8Encoding](xref:System.Text.UTF8Encoding) を選択してください。 この 2 つのエンコーディングは、ASCII 文字セットに対する動作は変わりませんが、[UTF8Encoding](xref:System.Text.UTF8Encoding) には次のような利点があります。 

* すべての Unicode 文字を表現できます ([ASCIIEncoding](xref:System.Text.ASCIIEncoding) でサポートされているのは U+0000 ～ U+007F の Unicode 文字値だけです)。

* エラー検出に対応しており、セキュリティも強化されます。

* できるだけ高速になるように調整されているため、他のエンコーディングよりも高速です。 全体が ASCII のコンテンツの場合でも、[UTF8Encoding](xref:System.Text.UTF8Encoding) で実行される演算は、[ASCIIEncoding](xref:System.Text.ASCIIEncoding) で実行される演算よりも高速になります。

[ASCIIEncoding](xref:System.Text.ASCIIEncoding) は、レガシ アプリケーションの場合にのみ使用を検討するようにしてください。 ただし、レガシ アプリケーションでも、次のような理由で [UTF8Encoding](xref:System.Text.UTF8Encoding) の方が適していることもあります (既定の設定の場合)。

* 厳密には ASCII でないコンテンツがアプリケーションに含まれている場合、それを [ASCIIEncoding](xref:System.Text.ASCIIEncoding) でエンコードすると、ASCII 以外の各文字は疑問符 (?) としてエンコードされます。 アプリケーションがこのデータをデコードすると、情報は失われます。


* 厳密には ASCII でないコンテンツがアプリケーションに含まれている場合、それを [UTF8Encoding](xref:System.Text.UTF8Encoding) でエンコードすると、結果を ASCII として解釈しようとしても一見理解不能になります。 ただし、アプリケーションがこのデータを UTF-8 デコーダーを使用してデコードすると、データのラウンド トリップが正常に行われます。

Web アプリケーションでは、Web 要求への応答としてクライアントに送信される文字に、クライアントで使用されているエンコーディングが反映されるようにする必要があります。 ほとんどの場合は、ユーザーが期待するエンコーディングでテキストを表示するために、[HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) プロパティを [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) プロパティの戻り値に設定する必要があります。

## <a name="using-an-encoding-object"></a>エンコーディング オブジェクトの使用

エンコーダーは、文字列 (通常は Unicode 文字) を対応する数値 (バイト) に変換します。 たとえば、ASCII エンコーダーを使用すると、Unicode 文字を ASCII に変換してコンソールに表示することができます。 この変換を実行するには、[Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) メソッドを呼び出します。 エンコードされた文字列を格納するために必要なバイト数をエンコードの実行前に確認するには、[GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) メソッドを呼び出します。

次の例では、1 つのバイト配列を使用して、文字列を 2 つの個別の操作でエンコードしています。 バイト配列内の次の ASCII エンコード済みバイト セットの開始位置を示すインデックスが保持されています。 この例では、[ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) メソッドを呼び出して、エンコードされた文字列を格納するために十分な大きさがバイト配列にあるかどうかを確認します。 次に、[ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) メソッドを呼び出して、文字列内の文字をエンコードします。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

デコーダーは、特定の文字エンコーディングが反映されたバイト配列を、文字配列または文字列の一連の文字に変換します。 バイト配列を文字配列にデコードするには、[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドを呼び出します。 バイト配列を文字列にデコードするには、[GetString](xref:System.Text.Encoding.GetString(System.Byte[])) メソッドを呼び出します。 デコードされたバイトを格納するために必要な文字数をデコードの実行前に確認するには、[GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) メソッドを呼び出します。

次の例では、3 つの文字列をエンコードした後、1 つの文字配列にデコードしています。 文字配列内の次のデコード済み文字セットの開始位置を示すインデックスが保持されています。 この例では、[GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) メソッドを呼び出して、デコードされたすべての文字を格納するために十分な大きさが文字配列にあるかどうかを確認します。 次に、[ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドを呼び出して、バイト配列をデコードします。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

[Encoding](xref:System.Text.Encoding) から派生するクラスのエンコード メソッドとデコード メソッドは、データ全体を処理するように設計されています。つまり、エンコードまたはデコードするすべてのデータが 1 回のメソッド呼び出しで渡されます。 ただし、場合によっては、データがストリームで提供され、エンコードまたはデコードするデータを複数の読み取り操作で取得しなければならないこともあります。 このような場合は、エンコード操作またはデコード操作で、前回の実行時に保存した状態を呼び出す必要があります。 [Encoder](xref:System.Text.Encoder) および [Decoder](xref:System.Text.Decoder) から派生するクラスのメソッドでは、複数のメソッド呼び出しにまたがるエンコード操作とデコード操作を処理できます。

特定のエンコーディングの [Encoder](xref:System.Text.Encoder) オブジェクトは、そのエンコーディングの [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) プロパティから取得できます。 特定のエンコーディングの [Decoder](xref:System.Text.Decoder) オブジェクトは、そのエンコーディングの [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) プロパティから取得できます。 デコード操作の場合、[Decoder](xref:System.Text.Decoder) から派生するクラスに含まれるのは [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドで、[Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])) に対応するメソッドはありません。

次の例は、Unicode のバイト配列のデコードに [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドを使用する場合と [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドを使用する場合の違いを示しています。 この例では、いくつかの Unicode 文字を含む文字列をファイルにエンコードした後、この 2 つのデコード メソッドを使用して一度に 10 バイトずつデコードしています。 10 番目と 11 番目のバイトに出現するサロゲート ペアは、別のメソッド呼び出しでデコードされます。 出力を見るとわかるように、[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドではこれらのバイトが正しくデコードされず、U+FFFD (REPLACEMENT CHARACTER) に置き換えられます。 一方、[Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドでは、このバイト配列が正しくデコードされて、元の文字列を取得できます。

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a>フォールバック ストラテジの選択

メソッドから文字のエンコードまたはデコードを行おうとしたときにマッピングが存在しない場合は、失敗したマッピングの処理方法を決めるフォールバック ストラテジを実装する必要があります。 次の 3 種類のフォールバック ストラテジがあります。 

* 最適フォールバック

* 置換フォールバック

* 例外フォールバック

> [!IMPORTANT]
> エンコード操作で最も一般的な問題は、Unicode 文字を特定のコード ページ エンコーディングにマップできない場合に発生します。 デコード操作で最も一般的な問題は、無効なバイト シーケンスを有効な Unicode 文字に変換できない場合に発生します。 そのため、個々のエンコーディング オブジェクトで使用されるフォールバック ストラテジを把握しておく必要があります。 エンコーディング オブジェクトをインスタンス化するときには、可能な限り、そのオブジェクトで使用されるフォールバック ストラテジを指定するようにしてください。
 
### <a name="best-fit-fallback"></a>最適フォールバック

ターゲット エンコード内に厳密な一致がない文字について、エンコーダーは類似した文字へのマッピングを試みることができます  (最適フォールバックは主にエンコード時の問題であり、デコード時の問題ではありません。 Unicode に正常にマッピングできない文字を含むコード ページはほとんどありません)。最適フォールバックは、[Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) および [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) の各オーバーロードによって取得されるコード ページ エンコーディングと 2 バイト文字セット エンコーディングの既定のフォールバック ストラテジです。

> [!NOTE]
> .NET の Unicode エンコーディング クラス ([UTF8Encoding](xref:System.Text.UTF8Encoding)、[UnicodeEncoding](xref:System.Text.UnicodeEncoding)、および [UTF32Encoding](xref:System.Text.UTF32Encoding)) では、理論上すべての文字セットのすべての文字がサポートされているため、これらのクラスを使用すると最適フォールバックの問題を解消できます。 
 

最適なストラテジはコード ページごとに異なるため、詳細には文書化されていません。 たとえば、全角のアルファベットがより一般的な半角のアルファベットにマッピングされるコード ページもあれば、 そのようなマッピングが行われないコード ページもあります。 積極的な最適ストラテジでも、一部のエンコーディングの一部の文字には可能な対応がない場合があります。 たとえば、中国語の漢字からコード ページ 1252 への適切なマッピングはありません。 その場合は、置換文字列が使用されます。 既定では、この文字列は単一の QUESTION MARK (疑問符) (U+003F) です。

次の例では、コード ページ 1252 (西ヨーロッパ言語の Windows コード ページ) を使用して、最適マッピングとその欠点を示しています。 まず、[Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) メソッドを使用して、コード ページ 1252 のエンコーディング オブジェクトを取得します。 このエンコーディング オブジェクトは、サポートされていない Unicode 文字に対して既定で最適マッピングを使用します。 次に、スペースで区切られた 3 つの非 ASCII 文字 (CIRCLED LATIN CAPITAL LETTER S (U+24C8)、SUPERSCRIPT FIVE (U+2075)、および INFINITY (U+221E)) を含む文字列をインスタンス化します。 出力を見るとわかるように、この文字列をエンコードすると、スペースを除く元の 3 つの文字が、QUESTION MARK (U+003F)、DIGIT FIVE (U+0035)、および DIGIT EIGHT (U+0038) に置き換えられます。 DIGIT EIGHT は、サポートされていない INFINITY 文字の代替として最適とは言えません。QUESTION MARK は、元の文字に対応するマッピングがなかったことを示します。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

最適マッピングは、Unicode データをコード ページ データにエンコードする [Encoding](xref:System.Text.Encoding) オブジェクトの既定の動作です。レガシ アプリケーションの中には、この動作に依存するものがあります。 ただし、ほとんどの新しいアプリケーションでは、セキュリティ上の理由から、最適動作の使用を避ける必要があります。 たとえば、アプリケーションで、最適エンコードを使用してドメイン名を付けないでください。

> [!Note]
> エンコーディングに対してカスタムの最適フォールバック マッピングを実装することもできます。 詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。
 
エンコーディング オブジェクトの既定値が最適フォールバックである場合、[Encoding](xref:System.Text.Encoding) オブジェクトを取得するときに別のフォールバック ストラテジを選択することもできます。そのためには、[Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) または [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) のオーバーロードを呼び出します。 次のセクションでは、コード ページ 1252 にマップできない文字をアスタリスク (\*) に置き換える例を紹介します。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a>置換フォールバック

ターゲット スキームに厳密な一致がなく、マップできる適切な文字もない文字について、アプリケーションで置換文字または置換文字列を指定することができます。 これは Unicode デコーダーの既定の動作です。Unicode デコーダーでは、デコードできない 2 バイトのシーケンスが REPLACEMENT_CHARACTER (U+FFFD) に置き換えられます。 また、[ASCIIEncoding](xref:System.Text.ASCIIEncoding) クラスの既定の動作でもあり、その場合はエンコードまたはデコードできない文字が疑問符に置き換えられます。 次の例は、前の例の Unicode 文字列に対する文字置換を示しています。 出力を見るとわかるように、ASCII バイト値にデコードできない文字は 0x3F (疑問符に対応する ASCII コード) に置き換えられます。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

.NET には、エンコード操作またはデコード操作で正確にマップできない文字を置換文字列に置き換える [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) クラスと [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) クラスが含まれています。 この置換文字列は、既定では疑問符ですが、クラス コンストラクターのオーバーロードを呼び出して別の文字列を選択することもできます。 通常は単一の文字を使用しますが、単一でなくてもかまいません。 次の例では、置換文字列としてアスタリスク (\*) を使用する [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) オブジェクトをインスタンス化して、コード ページ 1252 のエンコーダーの動作を変更しています。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> エンコーディング用の置換クラスを実装することもできます。 詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。
 
置換文字列としては、QUESTION MARK (U+003F) のほか、特に Unicode 文字列に正しく変換できないバイト シーケンスをデコードする場合に、Unicode REPLACEMENT CHARACTER (U+FFFD) がよく使用されます。 ただし、置換文字列は自由に選択できます。置換文字列に複数の文字を含めることもできます。

### <a name="exception-fallback"></a>例外フォールバック

最適フォールバックや置換文字列を提供する代わりに、エンコーダーで一連の文字をエンコードできない場合に [EncoderFallbackException](xref:System.Text.EncoderFallbackException) をスローしたり、デコーダーでバイト配列をデコードできない場合に [DecoderFallbackException](xref:System.Text.DecoderFallbackException) をスローしたりすることもできます。 エンコードおよびデコード操作で例外をスローするには、[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトをそれぞれ [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに指定します。 次の例は、ASCIIEncoding クラスによる例外フォールバックを示しています。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> エンコード操作用のカスタム例外ハンドラーを実装することもできます。 詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。
 
[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトは、例外を引き起こした状況について以下の情報を提供します。 

* [EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトに含まれている [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) メソッドにより、エンコードできない文字が不明なサロゲート ペアか (この場合は `true` が返されます)、不明な単一文字か (この場合は `false` が返されます) が示されます。 サロゲート ペアの文字は、[EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) プロパティと [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) プロパティから取得できます。 不明な単一文字は、[EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) プロパティから取得できます。 また、[EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) プロパティにより、エンコードできない最初の文字が見つかった文字列内の位置が示されます。

* [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトに含まれている [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) プロパティにより、デコードできないバイト配列が返されます。 また、[DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) プロパティにより、不明なバイトの開始位置が示されます。

[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトでは、例外に関する診断情報は十分に入手できますが、エンコード バッファーやデコード バッファーにアクセスすることはできません。 したがって、エンコード メソッド内またはデコード メソッド内で無効なデータを置換したり修正したりすることはできません。

## <a name="implementing-a-custom-fallback-strategy"></a>カスタム フォールバック ストラテジの実装

.NET には、コード ページによって内部的に実装される最適マッピングに加えて、フォールバック ストラテジを実装するための次のクラスが含まれています。

* [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) および [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。エンコード操作中に文字を置換します。

* [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) および [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer)。デコード操作中に文字を置換します。

* [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) および [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。文字をエンコードできない場合に [EncoderFallbackException](xref:System.Text.EncoderFallbackException) をスローします。

* [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) および [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer)。文字をエンコードできない場合に [DecoderFallbackException](xref:System.Text.DecoderFallbackException) をスローします。

さらに、次の手順に従って、最適フォールバック、置換フォールバック、または例外フォールバックを使用するカスタム ソリューションを実装できます。 

1. エンコード操作の場合は [EncoderFallback](xref:System.Text.EncoderFallback)、デコード操作の場合は [DecoderFallback](xref:System.Text.DecoderFallback) の派生クラスを作成します。

2. エンコード操作の場合は [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)、デコード操作の場合は [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) の派生クラスを作成します。

3. 例外フォールバックにおいて、あらかじめ定義されている [EncoderFallbackException](xref:System.Text.EncoderFallbackException) クラスと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) クラスが目的に合わない場合は、[Exception](xref:System.Exception) や [ArgumentException](xref:System.ArgumentException) などの例外オブジェクトから派生クラスを作成します。

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>EncoderFallback または DecoderFallback からの派生

カスタム フォールバック ソリューションを実装するには、エンコード操作の場合は [EncoderFallback](xref:System.Text.EncoderFallback)、デコード操作の場合は [DecoderFallback](xref:System.Text.DecoderFallback) を継承するクラスを作成する必要があります。 これらのクラスのインスタンスは [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに渡され、エンコーディング クラスとフォールバックの実装の仲介役として機能します。

エンコーダーまたはデコーダーのカスタム フォールバック ソリューションを作成するときには、次のメンバーを実装する必要があります。

* [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) プロパティまたは [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) プロパティ。最適、置換、例外の各フォールバックで単一の文字を置き換えるために返すことのできる文字の最大数を返します。 カスタム例外フォールバックの場合は 0 になります。 

* [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) メソッドまたは [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) メソッド。[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) または [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) のカスタム実装を返します。 このメソッドは、エンコーダーで正しくエンコードできない文字が初めて検出されたとき、またはデコーダーで正しくデコードできないバイトが初めて検出されたときに呼び出されます。

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>EncoderFallbackBuffer または DecoderFallbackBuffer からの派生

カスタム フォールバック ソリューションを実装するには、エンコード操作の場合は [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)、デコード操作の場合は [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) を継承するクラスも作成する必要があります。 これらのクラスのインスタンスは、[EncoderFallback](xref:System.Text.EncoderFallback) クラスおよび [DecoderFallback](xref:System.Text.DecoderFallback) クラスの `CreateFallbackBuffer` メソッドによって返されます。 [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) メソッドは、エンコーダーでエンコードできない文字が初めて検出されたときに呼び出され、[DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) メソッドは、デコーダーでデコードできないバイトが検出されたときに呼び出されます。 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) クラスと[DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) クラスは、フォールバックの実装を提供します。 各インスタンスは、エンコードできない文字またはデコードできないバイト シーケンスを置き換えるフォールバック文字を含むバッファーを表します。

エンコーダーまたはデコーダーのカスタム フォールバック ソリューションを作成するときには、次のメンバーを実装する必要があります。

* [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) メソッドまたは [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) メソッド。 [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) は、エンコーダーによって呼び出され、エンコードできない文字に関する情報をフォールバック バッファーに提供します。 エンコードされる文字はサロゲート ペアである場合もあるため、このメソッドはオーバーロードされます。 最初のオーバーロードには、エンコードされる文字と、その文字列内のインデックスが渡されます。 2 番目のオーバーロードには、上位および下位のサロゲートと、その文字列内のインデックスが渡されます。 [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) メソッドは、デコーダーによって呼び出され、デコードできないバイトに関する情報をフォールバック バッファーに提供します。 このメソッドには、デコードできないバイト配列と、最初のバイトのインデックスが渡されます。 フォールバック メソッドは、フォールバック バッファーが最適な文字または置換文字を提供できる場合は `true`、それ以外の場合は `false` を返します。 例外フォールバックの場合は例外をスローします。

* [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) メソッドまたは [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) メソッド。フォールバック バッファーから次の文字を取得するために、エンコーダーまたはデコーダーによって繰り返し呼び出されます。 すべてのフォールバック文字を返し終わったら、このメソッドは U+0000 を返す必要があります。 

* [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) プロパティまたは [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) プロパティ。フォールバック バッファー内の残りの文字数を返します。

* [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) メソッドまたは [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) メソッド。フォールバック バッファー内の現在の位置を前の文字に移動します。

* [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) メソッドまたは [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) メソッド。フォールバック バッファーを再初期化します。

フォールバックの実装が最適フォールバックまたは置換フォールバックの場合は、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) と [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) の派生クラスで、2 つのプライベート インスタンス フィールド (バッファー内の正確な文字数と、次に返される文字のインデックス) も保持します。

### <a name="an-encoderfallback-example"></a>EncoderFallback の例

前の例では、置換フォールバックを使用して、対応する ASCII 文字がない Unicode 文字をアスタリスク (\*) に置き換えました。 次の例では、代わりに最適フォールバックのカスタム実装を使用して、非 ASCII 文字のマッピングを改善しています。

次のコードでは、[EncoderFallback](xref:System.Text.EncoderFallback) から派生する `CustomMapper` という名前のクラスを定義して、非 ASCII 文字の最適マッピングを処理します。 このクラスの `CreateFallbackBuffer` メソッドは、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) の実装を提供する `CustomMapperFallbackBuffer` オブジェクトを返します。 `CustomMapper` クラスは、[Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) オブジェクトを使用して、サポートされていない Unicode 文字 (キー値) と、それらに対応する 8 ビット文字とのマッピングを格納します (64 ビット整数の 2 つの連続するバイトに格納されます)。 このマッピングをフォールバック バッファーで使用できるようにするには、`CustomMapper` のインスタンスを `CustomMapperFallbackBuffer` のクラス コンストラクターにパラメーターとして渡します。 最も長いマッピングは Unicode 文字 U+221E に対応する文字列 "INF" なので、`MaxCharCount` プロパティは 3 を返します。 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

次のコードでは、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) から派生する `CustomMapperFallbackBuffer` クラスを定義しています。 `CustomMapper` インスタンスで定義されている、最適マッピングを含むディクショナリは、クラス コンストラクターから取得できます。 このクラスの `Fallback` メソッドは、ASCII エンコーダーでエンコードできない Unicode 文字がマッピング ディクショナリで定義されている場合は `true` を返し、それ以外の場合は `false` を返します。 フォールバックのたびに、プライベート変数 `count` は返される残りの文字数を示し、プライベート変数 `index` は次に返される文字の文字列バッファー内 (`charsToReturn` 内) の位置を示します。 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

次のコードでは、`CustomMapper` オブジェクトをインスタンス化して、そのインスタンスを [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに渡しています。 出力を見るとわかるように、この最適フォールバックの実装では、元の文字列の 3 つの非 ASCII 文字が正しく処理されます。

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a>関連項目

[System.Text.Encoder](xref:System.Text.Encoder)

[System.Text.EncoderFallback](xref:System.Text.EncoderFallback)

[System.Text.Decoder](xref:System.Text.Decoder)

[System.Text.DecoderFallback](xref:System.Text.DecoderFallback)

[System.Text.Encoding](xref:System.Text.Encoding)







<!--HONumber=Nov16_HO3-->


