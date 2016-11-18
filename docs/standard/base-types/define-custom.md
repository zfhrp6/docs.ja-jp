---
title: "方法: カスタム数値書式プロバイダーを定義して使用する"
description: "方法: カスタム数値書式プロバイダーを定義して使用する"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9b184114-6612-4c1a-a2db-2e24e65b0f77
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: bb62bdd03d4af4f764ac3bc8734c67902fffa798

---

# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>方法: カスタム数値書式プロバイダーを定義して使用する

.NET では、数値の文字列形式を広範囲に制御できます。 数値の書式をカスタマイズするため、次の機能をサポートしています。

* 標準の数値書式指定文字列: 数値をその文字列形式に変換するための定義済みの書式セットを提供します。 これらは、format パラメーターを持つ [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)) などの任意の数値書式指定メソッドと共に使用できます。 詳細については、「[標準の数値書式指定文字列](standard-numeric.md)」を参照してください。

* カスタム数値書式指定文字列: カスタム数値書式指定子を定義するために結合できる記号のセットを提供します。 これらは、format パラメーターを持つ [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)) などの任意の数値書式指定メソッドでも使用できます。 詳細については、「[カスタム数値書式指定文字列](custom-numeric.md)」を参照してください。

* カスタムの [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトまたは [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト: 記号を定義し、数値の文字列形式を表示するために使用されるパターンの書式を設定します。 これらは、*provider* パラメーターを持つ [ToString](xref:System.Int32.ToString(System.IFormatProvider)) などの数値書式指定メソッドと共に使用できます。 通常、*provider* パラメーターは、カルチャに固有の書式を指定するために使用されます。

一部の例には (アプリケーションで書式設定されたアカウント番号や ID 番号、郵便番号を表示する必要がある場合など)、これら 3 つの方法は適していません。 .NET では、[CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトでも [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトでもない書式設定オブジェクトを定義して、数値を書式設定する方法を決定することもできます。 このトピックでは、このようなオブジェクトを実装するため、詳細な手順を説明し、電話番号の書式を設定する例について説明します。

## <a name="to-define-a-custom-format-provider"></a>カスタム書式プロバイダーを定義するには

1. [IFormatProvider](xref:System.IFormatProvider) インターフェイスと [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを実装するクラスを定義します。 

2. [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドを実装します。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) は、書式指定メソッド ([String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドなど) が実際にカスタム書式設定の実行を担当するオブジェクトを取得するために呼び出すコールバック メソッドです。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の一般的な実装は、次のとおりです。

    a.  [Type](xref:System.Type) オブジェクトを [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスとして表すメソッド パラメーターとして渡すかどうかを決定します。
    
    b.  パラメーターが [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを表す場合、[GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) はカスタム書式設定の提供を担当する [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを実装するオブジェクトを返します。 通常、カスタム書式指定オブジェクトは、それ自体を返します。 
    
    c. パラメーターが [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを表していない場合、[GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) は `null` を返します。
    
3. [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドを実装します。 このメソッドは、[String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドによって呼び出され、数値の文字列形式を返します。 メソッドの実装には通常、次の作業を行います。

    a.  必要に応じて、*provider* パラメーターを調べることで、メソッドが書式指定サービスを提供する正当なものであることを確認します。 [IFormatProvider](xref:System.IFormatProvider) と [ICustomFormatter](xref:System.ICustomFormatter) の両方を実装する書式設定オブジェクトの場合、現在の書式設定オブジェクトと等しいことを確認するため、*provider* パラメーターをテストする必要があります。
    
    b.  書式指定オブジェクトが、カスタム書式指定子をサポートするかどうかを決定します  (たとえば、"N" 書式指定子は、米国の電話番号を NANP 形式で出力することを示し、"I" はITU-T 推奨 E.123 形式での出力を示すことができます)。書式指定子を使用している場合、メソッドが特定の書式指定子を処理する必要があります。 これが format パラメーターでメソッドに渡されます。 指定子がない場合、*format* パラメーターの値は [String.Empty](xref:System.String#System_String_Empty) です。
    
    c. *arg* パラメーターとしてメソッドに渡される数値を取得します。 文字列形式に変換するために必要な操作を実行します。
    
    d. *arg* パラメーターの文字列表現を返します。
    
## <a name="to-use-a-custom-numeric-formatting-object"></a>カスタム数値書式設定オブジェクトを使用するには

1. カスタム書式指定クラスの新しいインスタンスを作成します。

2. それをカスタム書式指定オブジェクト、書式指定子 (使用されていない場合は [String.Empty](xref:System.String.Empty))、および書式設定する数値に渡す、[String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 書式指定メソッドを呼び出します。 

## <a name="example"></a>例

次の例では、米国の電話番号を表す数値を NANP または E.123 形式に変換する、`TelephoneFormatter` という名前のカスタム数値書式プロバイダーを定義します。 このメソッドは、"N" (NANP 形式を出力) と "I" (国際 E.123 形式を出力) の 2 つの書式指定子を処理します。

```csharp
using System;
using System.Globalization;

public class TelephoneFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   {
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }               

   public string Format(string format, object arg, IFormatProvider formatProvider)
   {
      // Check whether this is an appropriate callback             
      if (! this.Equals(formatProvider))
         return null; 

      // Set default format specifier             
      if (string.IsNullOrEmpty(format)) 
         format = "N";

      string numericString = arg.ToString();

      if (format == "N")
      {
         if (numericString.Length <= 4)
            return numericString;
         else if (numericString.Length == 7)
            return numericString.Substring(0, 3) + "-" + numericString.Substring(3, 4); 
         else if (numericString.Length == 10)
               return "(" + numericString.Substring(0, 3) + ") " +
                      numericString.Substring(3, 3) + "-" + numericString.Substring(6);   
         else
            throw new FormatException( 
                      string.Format("'{0}' cannot be used to format {1}.", 
                                    format, arg.ToString()));
      }
      else if (format == "I")
      {
         if (numericString.Length < 10)
            throw new FormatException(string.Format("{0} does not have 10 digits.", arg.ToString()));
         else
            numericString = "+1 " + numericString.Substring(0, 3) + " " + numericString.Substring(3, 3) + " " + numericString.Substring(6);
      }
      else
      {
         throw new FormatException(string.Format("The {0} format specifier is invalid.", format));
      } 
      return numericString;  
   }
}

public class TestTelephoneFormatter
{
   public static void Main()
   {
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:I}", 4257884748));
   }
}
```

```vb
Public Class TelephoneFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If               
   End Function               

   Public Function Format(fmt As String, arg As Object, _
                          formatProvider As IFormatProvider) As String _
                   Implements ICustomFormatter.Format
      ' Check whether this is an appropriate callback             
      If Not Me.Equals(formatProvider) Then Return Nothing 

      ' Set default format specifier             
      If String.IsNullOrEmpty(fmt) Then fmt = "N"

      Dim numericString As String = arg.ToString

      If fmt = "N" Then
         Select Case numericString.Length
            Case <= 4 
               Return numericString
            Case 7
               Return Left(numericString, 3) & "-" & Mid(numericString, 4) 
            Case 10
               Return "(" & Left(numericString, 3) & ") " & _
                      Mid(numericString, 4, 3) & "-" & Mid(numericString, 7)   
            Case Else
               Throw New FormatException( _
                         String.Format("'{0}' cannot be used to format {1}.", _
                                       fmt, arg.ToString()))
         End Select
      ElseIf fmt = "I" Then
         If numericString.Length < 10 Then
            Throw New FormatException(String.Format("{0} does not have 10 digits.", arg.ToString()))
         Else
            numericString = "+1 " & Left(numericString, 3) & " " & Mid(numericString, 4, 3) & " " & Mid(numericString, 7)
         End If      
      Else
         Throw New FormatException(String.Format("The {0} format specifier is invalid.", fmt))
      End If 
      Return numericString  
   End Function
End Class

Public Module TestTelephoneFormatter
   Public Sub Main
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:I}", 4257884748))
   End Sub
End Module
```

カスタム数値書式プロバイダーは、[String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドでのみ使用できます。 [IFormatProvider](xref:System.IFormatProvider) 型のパラメーターがある数値書式指定メソッド (`ToString` など) の他のオーバーロードはすべて、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 型を表す [Type](xref:System.Type) オブジェクトの [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 実装を渡します。 代わりに、これらはメソッドが [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを返すことを期待します。 そうでない場合、カスタム数値書式プロバイダーは無視され、現在のカルチャの [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトがその代わりに使用されます。 この例では、メソッド パラメーターを検査し、[ICustomFormatter](xref:System.ICustomFormatter) 以外の型を表す場合には *null* を返すことで、`TelephoneFormatter.GetFormat` メソッドはそれが書式指定メソッドに不適切に渡される可能性を処理します。

カスタム数値書式プロバイダーが一連の書式指定子をサポートしている場合、[String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドの呼び出しで使用される書式指定項目で書式指定子が指定されていない場合に、既定の動作を提供することを確認します。 例では、"N" が既定の書式指定子です。 これにより、明示的な書式指定子を提供することによって、数値を書式設定された電話番号に変換できます。 このようなメソッドの呼び出しの例を次に示します。

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))
```

ただし、書式指定子が存在しない場合に、変換を行うようにすることもできます。 このようなメソッドの呼び出しの例を次に示します。

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))
```

既定の書式指定子が定義されていない場合、[ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドの実装には、使用しているコードでサポートされていない書式設定を .NET が提供できるように、次のようなコードを含める必要があります。

```csharp
if (arg is IFormattable) 
   s = ((IFormattable)arg).ToString(format, formatProvider);
else if (arg != null)    
   s = arg.ToString();
```

```vb
If TypeOf(arg) Is IFormattable Then 
   s = DirectCast(arg, IFormattable).ToString(fmt, formatProvider)
ElseIf arg IsNot Nothing Then    
   s = arg.ToString()
End If
```

この例の場合、[ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) を実装するメソッドは、[String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドのコールバック メソッドとして機能することを意図しています。 そのため、*formatProvider* パラメーターを調べ、現在の `TelephoneFormatter` オブジェクトへの参照が含まれるかどうかを判断します。 ただし、メソッドはコードから直接呼び出すこともできます。 その場合は、*formatProvider* パラメーターを使用して、カルチャに固有の書式情報を提供する [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトまたは [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを提供することができます。

## <a name="see-also"></a>関連項目

[書式設定操作の実行](performing-formatting-operations.md)



<!--HONumber=Nov16_HO3-->


