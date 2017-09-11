---
title: "型の書式設定"
description: "型の書式設定"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
ms.translationtype: Human Translation
ms.sourcegitcommit: b967d8e55347f44a012e4ad8e916440ae228c8ec
ms.openlocfilehash: e9b8ad13a48dd43236769b130d6f8a75b7b023ca
ms.contentlocale: ja-jp
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-types"></a><span data-ttu-id="32c63-104">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-104">Formatting types</span></span>

<span data-ttu-id="32c63-105">書式設定とはクラス、構造体、または列挙値のインスタンスを文字列形式に変換するプロセスのことで、多くの場合、変換した文字列をユーザーに表示したり、逆シリアル化して元のデータ型を復元したりするために行います。</span><span class="sxs-lookup"><span data-stu-id="32c63-105">Formatting is the process of converting an instance of a class, structure, or enumeration value to its string representation, often so that the resulting string can be displayed to users or deserialized to restore the original data type.</span></span> <span data-ttu-id="32c63-106">この変換には次のような問題がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-106">This conversion can pose a number of challenges:</span></span>

* <span data-ttu-id="32c63-107">値の内部での格納方法に、ユーザーが望む表示方法が反映されない場合がある。</span><span class="sxs-lookup"><span data-stu-id="32c63-107">The way that values are stored internally does not necessarily reflect the way that users want to view them.</span></span> <span data-ttu-id="32c63-108">たとえば、電話番号が **8009999999** という形式で格納されることがあります。これではユーザーにはわかりにくいため、</span><span class="sxs-lookup"><span data-stu-id="32c63-108">For example, a telephone number might be stored in the form **8009999999**, which is not user-friendly.</span></span> <span data-ttu-id="32c63-109">代わりに **800-999-9999** と表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-109">It should instead be displayed as **800-999-9999**.</span></span> <span data-ttu-id="32c63-110">数値をこのように書式指定する例については、「[カスタム書式指定文字列](#custom-format-strings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-110">See the [Custom format strings](#custom-format-strings) section for an example that formats a number in this way.</span></span> 

* <span data-ttu-id="32c63-111">オブジェクトから文字列形式への変換が直観的に理解しづらい場合がある。</span><span class="sxs-lookup"><span data-stu-id="32c63-111">Sometimes the conversion of an object to its string representation is not intuitive.</span></span> <span data-ttu-id="32c63-112">たとえば、**Temperature** オブジェクトや **Person** オブジェクトの文字列形式がどのようになるのか、明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="32c63-112">For example, it is not clear how the string representation of a **Temperature** object or a **Person** object should appear.</span></span> <span data-ttu-id="32c63-113">**Temperature** オブジェクトをさまざまな方法で書式指定する例については、「[標準書式指定文字列](#standard-format-strings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-113">For an example that formats a **Temperature** object in a variety of ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

* <span data-ttu-id="32c63-114">通常、カルチャ依存の書式指定が必要になる。</span><span class="sxs-lookup"><span data-stu-id="32c63-114">Values often require culture-sensitive formatting.</span></span> <span data-ttu-id="32c63-115">たとえば、通貨値を数字で表すアプリケーションでは、数値文字列にカルチャ別の通貨記号、桁区切り記号 (ほとんどのカルチャでは 1000 単位)、および小数点を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-115">For example, in an application that uses numbers to reflect monetary values, numeric strings should include the current culture’s currency symbol, group separator (which, in most cultures, is the thousands separator), and decimal symbol.</span></span> <span data-ttu-id="32c63-116">例については、「[書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-116">For an example, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span> 

* <span data-ttu-id="32c63-117">アプリケーションによっては、同じ値をさまざまな方法で表示する必要がある。</span><span class="sxs-lookup"><span data-stu-id="32c63-117">An application may have to display the same value in different ways.</span></span> <span data-ttu-id="32c63-118">たとえば、列挙型のメンバーを表すために、その名前の文字列形式を表示する場合や、基になる値を表示する場合が考えられます。</span><span class="sxs-lookup"><span data-stu-id="32c63-118">For example, an application may represent an enumeration member by displaying a string representation of its name or by displaying its underlying value.</span></span> <span data-ttu-id="32c63-119">[DayOfWeek](xref:System.DayOfWeek) 列挙体のメンバーをさまざまな方法で書式指定する例については、「[標準書式指定文字列](#standard-format-strings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-119">For an example that formats a member of the [DayOfWeek](xref:System.DayOfWeek) enumeration in different ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

<span data-ttu-id="32c63-120">.NET は書式設定機能が充実しているため、開発者はこうした要件を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-120">.NET provides rich formatting support that enables developers to address these requirements.</span></span> 

> [!NOTE]
> <span data-ttu-id="32c63-121">書式設定は型の値を文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="32c63-121">Formatting converts the value of a type into a string representation.</span></span> <span data-ttu-id="32c63-122">解析は書式設定の逆の操作で、</span><span class="sxs-lookup"><span data-stu-id="32c63-122">Parsing is the inverse of formatting.</span></span> <span data-ttu-id="32c63-123">文字列形式からデータ型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="32c63-123">A parsing operation creates an instance of a data type from its string representation.</span></span> <span data-ttu-id="32c63-124">他のデータ型への文字列の変換については、「[文字列の解析](parsing-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-124">For information about converting strings to other data types, see [Parsing strings](parsing-strings.md).</span></span>

<span data-ttu-id="32c63-125">この概要は、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="32c63-125">This overview contains the following sections:</span></span>

* [<span data-ttu-id="32c63-126">.NET での書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-126">Formatting in .NET</span></span>](#formatting-in-net)

* [<span data-ttu-id="32c63-127">ToString メソッドを使用した既定の書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-127">Default formatting using the ToString method</span></span>](#default-formatting-using-the-tostring-method)

* [<span data-ttu-id="32c63-128">ToString メソッドのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="32c63-128">Overriding the ToString method</span></span>](#overriding-the-tostring-method)

* [<span data-ttu-id="32c63-129">ToString メソッドと書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-129">The ToString method and format strings</span></span>](#the-tostring-method-and-format-strings)

    * [<span data-ttu-id="32c63-130">標準の書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-130">Standard format strings</span></span>](#standard-format-strings)
    
    * [<span data-ttu-id="32c63-131">カスタム書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-131">Custom format strings</span></span>](#custom-format-strings)
    
    * [<span data-ttu-id="32c63-132">書式指定文字列と .NET 型</span><span class="sxs-lookup"><span data-stu-id="32c63-132">Format strings and .NET types</span></span>](#format-strings-and-net-types)
    
* [<span data-ttu-id="32c63-133">書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定</span><span class="sxs-lookup"><span data-stu-id="32c63-133">Culture-sensitive formatting with format providers and the IFormatProvider interface</span></span>](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [<span data-ttu-id="32c63-134">数値のカルチャに依存した書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-134">Culture-sensitive formatting of numeric values</span></span>](#culture-sensitive-formatting-of-numeric-values)
    
    * [<span data-ttu-id="32c63-135">日付と時刻の値のカルチャに依存した書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-135">Culture-sensitive formatting of date and time values</span></span>](#culture-sensitive-formatting-of-date-and-time-values)
    
* [<span data-ttu-id="32c63-136">IFormattable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32c63-136">The IFormattable interface</span></span>](#the-iformattable-interface)

* [<span data-ttu-id="32c63-137">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="32c63-137">Composite formatting</span></span>](#composite-formatting)

* [<span data-ttu-id="32c63-138">ICustomFormatter を使用したカスタム書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-138">Custom formatting with ICustomFormatter</span></span>](#custom-formatting-with-icustomformatter)

* [<span data-ttu-id="32c63-139">関連トピック</span><span class="sxs-lookup"><span data-stu-id="32c63-139">Related topics</span></span>](#related-topics)

* [<span data-ttu-id="32c63-140">参照</span><span class="sxs-lookup"><span data-stu-id="32c63-140">Reference</span></span>](#reference)

## <a name="formatting-in-net"></a><span data-ttu-id="32c63-141">.NET での書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-141">Formatting in .NET</span></span>

<span data-ttu-id="32c63-142">基本的な書式設定の方式は、[Object.ToString](xref:System.Object.ToString) メソッドによって既定として実装されます。このメソッドについては、このトピックの「[ToString メソッドを使用した既定の書式設定](#default-formatting-using-the-tostring-method)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-142">The basic mechanism for formatting is the default implementation of the [Object.ToString](xref:System.Object.ToString) method, which is discussed in the [Default formatting using the ToString method](#default-formatting-using-the-tostring-method) section later in this topic.</span></span> <span data-ttu-id="32c63-143">ただし、.NET には、この既定の書式設定機能を変更および拡張する方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="32c63-143">However, .NET provides several ways to modify and extend its default formatting support.</span></span> <span data-ttu-id="32c63-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-144">These include the following:</span></span>

* <span data-ttu-id="32c63-145">[Object.ToString](xref:System.Object.ToString) メソッドをオーバーライドして、オブジェクトの値のカスタム文字列形式を定義する方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-145">Overriding the [Object.ToString](xref:System.Object.ToString) method to define a custom string representation of an object’s value.</span></span> <span data-ttu-id="32c63-146">詳細については、このトピックの「[ToString メソッドのオーバーライド](#overriding-the-tostring-method)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-146">For more information, see the [Overriding the ToString method](#overriding-the-tostring-method) section later in this topic.</span></span>

* <span data-ttu-id="32c63-147">オブジェクトの値の文字列形式に複数の形式を持たせる書式指定子を定義する方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-147">Defining format specifiers that enable the string representation of an object’s value to take multiple forms.</span></span> <span data-ttu-id="32c63-148">たとえば、次のステートメントでは "X" 書式指定子を使用して整数を 16 進値の文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="32c63-148">For example, the "X" format specifier in the following statement converts an integer to the string representation of a hexadecimal value.</span></span>

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  <span data-ttu-id="32c63-149">書式指定子の詳細については、「[ToString メソッドと書式指定文字列](#the-tostring-method-and-format-strings)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-149">For more information about format specifiers, see the [The ToString method and format strings](#the-tostring-method-and-format-strings) section.</span></span>
  
* <span data-ttu-id="32c63-150">書式プロバイダーを使用して、特定のカルチャの書式指定規則を利用する方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-150">Using format providers to take advantage of the formatting conventions of a specific culture.</span></span> <span data-ttu-id="32c63-151">たとえば、次のステートメントでは en-US カルチャの書式指定規則を使用して通貨値を表示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-151">For example, the following statement displays a currency value by using the formatting conventions of the en-US culture.</span></span> 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  <span data-ttu-id="32c63-152">書式プロバイダーを使用した書式設定の詳細については、「[書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-152">For more information about formatting with format providers, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span>  
  
* <span data-ttu-id="32c63-153">[IFormattable](xref:System.IFormattable) インターフェイスを実装して、[Convert](xref:System.Convert) クラスによる文字列変換と複合書式指定の両方をサポートする方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-153">Implementing the [IFormattable](xref:System.IFormattable) interface to support both string conversion with the [Convert](xref:System.Convert) class and composite formatting.</span></span> <span data-ttu-id="32c63-154">詳細については、「[IFormattable インターフェイス](#the-iformattable-interface)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-154">For more information, see the [The IFormattable interface](#the-iformattable-interface) section.</span></span>

* <span data-ttu-id="32c63-155">複合書式指定を使用して、値の文字列形式を大きな文字列に埋め込む方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-155">Using composite formatting to embed the string representation of a value in a larger string.</span></span> <span data-ttu-id="32c63-156">詳細については、「[複合書式指定](#composite-formatting)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-156">For more information, see the [Composite formatting](#composite-formatting) section.</span></span>

* <span data-ttu-id="32c63-157">[ICustomFormatter](xref:System.ICustomFormatter) および [IFormatProvider](xref:System.IFormatProvider) を実装して、完全なカスタム書式設定ソリューションを提供する方法。</span><span class="sxs-lookup"><span data-stu-id="32c63-157">Implementing [ICustomFormatter](xref:System.ICustomFormatter) and [IFormatProvider](xref:System.IFormatProvider) to provide a complete custom formatting solution.</span></span> <span data-ttu-id="32c63-158">詳細については、「[ICustomFormatter を使用したカスタム書式設定](#custom-formatting-with-icustomformatter)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-158">For more information, see the [Custom formatting with ICustomFormatter](#custom-formatting-with-icustomformatter) section.</span></span>

<span data-ttu-id="32c63-159">以降のセクションでは、オブジェクトを文字列形式に変換するこれらの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-159">The following sections examine these methods for converting an object to its string representation.</span></span>

## <a name="default-formatting-using-the-tostring-method"></a><span data-ttu-id="32c63-160">ToString メソッドを使用した既定の書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-160">Default formatting using the ToString method</span></span>

<span data-ttu-id="32c63-161">[System.Object](xref:System.Object) から派生したすべての型は、既定で型の名前を返す、パラメーターなしの [ToString](xref:System.Object.ToString) メソッドを自動的に継承します。</span><span class="sxs-lookup"><span data-stu-id="32c63-161">Every type that is derived from [System.Object](xref:System.Object) automatically inherits a parameterless [ToString](xref:System.Object.ToString) method, which returns the name of the type by default.</span></span> <span data-ttu-id="32c63-162">既定の [ToString](xref:System.Object.ToString) メソッドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-162">The following example illustrates the default [ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="32c63-163">このコード例では、実装を持たない `Automobile` という名前のクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-163">It defines a class named `Automobile` that has no implementation.</span></span> <span data-ttu-id="32c63-164">このクラスがインスタンス化され、[ToString](xref:System.Object.ToString) メソッドが呼び出されると、その型の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-164">When the class is instantiated and its [ToString](xref:System.Object.ToString) method is called, it displays its type name.</span></span> <span data-ttu-id="32c63-165">サンプルでは、[ToString](xref:System.Object.ToString) メソッドが明示的に呼び出されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-165">Note that the [ToString](xref:System.Object.ToString) method is not explicitly called in the example.</span></span> <span data-ttu-id="32c63-166">[Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) メソッドは引数として渡されたオブジェクトの [ToString](xref:System.Object.ToString) メソッドを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32c63-166">The [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) method implicitly calls the [ToString](xref:System.Object.ToString) method of the object passed to it as an argument.</span></span> 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

<span data-ttu-id="32c63-167">インターフェイス以外の型はすべて [Object](xref:System.Object) から派生するため、この機能はカスタムのクラスまたは構造体に自動的に提供されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-167">Because all types other than interfaces are derived from [Object](xref:System.Object), this functionality is automatically provided to your custom classes or structures.</span></span> <span data-ttu-id="32c63-168">ただし、既定の [ToString](xref:System.Object.ToString) メソッドによって提供される機能には制限があり、型の識別は行いますが、型のインスタンスに関する情報は提供しません。</span><span class="sxs-lookup"><span data-stu-id="32c63-168">However, the functionality offered by the default [ToString](xref:System.Object.ToString) method, is limited: Although it identifies the type, it fails to provide any information about an instance of the type.</span></span> <span data-ttu-id="32c63-169">それ自体に関する情報を提供するオブジェクトの文字列形式を提供するには、[ToString](xref:System.Object.ToString) メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-169">To provide a string representation of an object that provides information about that object, you must override the [ToString](xref:System.Object.ToString) method.</span></span>

> [!NOTE]
> <span data-ttu-id="32c63-170">構造体は、[Object](xref:System.Object) から派生した [ValueType](xref:System.ValueType) を継承します。</span><span class="sxs-lookup"><span data-stu-id="32c63-170">Structures inherit from [ValueType](xref:System.ValueType), which in turn is derived from [Object](xref:System.Object).</span></span> <span data-ttu-id="32c63-171">[ValueType](xref:System.ValueType) は [Object.ToString](xref:System.Object.ToString) をオーバーライドしますが、その実装は同じです。</span><span class="sxs-lookup"><span data-stu-id="32c63-171">Although [ValueType](xref:System.ValueType) overrides [Object.ToString](xref:System.Object.ToString), its implementation is identical.</span></span>

## <a name="overriding-the-tostring-method"></a><span data-ttu-id="32c63-172">ToString メソッドのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="32c63-172">Overriding the ToString method</span></span>

<span data-ttu-id="32c63-173">型の名前の表示は用途が限定され、型のコンシューマー側でインスタンスを別のインスタンスと区別することはできません。</span><span class="sxs-lookup"><span data-stu-id="32c63-173">Displaying the name of a type is often of limited use and does not allow consumers of your types to differentiate one instance from another.</span></span> <span data-ttu-id="32c63-174">ただし、[ToString](xref:System.Object.ToString) メソッドをオーバーライドして、より役に立つオブジェクトの値の形式を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-174">However, you can override the [ToString](xref:System.Object.ToString) method to provide a more useful representation of an object’s value.</span></span> <span data-ttu-id="32c63-175">次の例では `Temperature` オブジェクトを定義し、その [ToString](xref:System.Object.ToString) メソッドをオーバーライドして、温度を摂氏で表示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-175">The following example defines a `Temperature` object and overrides its [ToString](xref:System.Object.ToString) method to display the temperature in degrees Celsius.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

<span data-ttu-id="32c63-176">.NET では、各プリミティブ値型の [ToString](xref:System.Object.ToString) メソッドは名前の代わりにオブジェクトの値を表示するようにオーバーライドされています。</span><span class="sxs-lookup"><span data-stu-id="32c63-176">In .NET, the [ToString](xref:System.Object.ToString) method of each primitive value type has been overridden to display the object’s value instead of its name.</span></span> <span data-ttu-id="32c63-177">各プリミティブ型のオーバーライドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-177">The following table shows the override for each primitive type.</span></span> <span data-ttu-id="32c63-178">オーバーライドされているメソッドのほとんどは [ToString](xref:System.Object.ToString) メソッドの別のオーバーロードを呼び出し、それにその型の一般書式を定義する "G" 書式指定子と、現在のカルチャを表す [IFormatProvider](xref:System.IFormatProvider) オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="32c63-178">Note that most of the overridden methods call another overload of the [ToString](xref:System.Object.ToString) method and pass it the "G" format specifier, which defines the general format for its type, and an [IFormatProvider](xref:System.IFormatProvider) object that represents the current culture.</span></span>

<span data-ttu-id="32c63-179">型</span><span class="sxs-lookup"><span data-stu-id="32c63-179">Type</span></span> | <span data-ttu-id="32c63-180">ToString のオーバーライド</span><span class="sxs-lookup"><span data-stu-id="32c63-180">ToString override</span></span>
---- | -----------------
[<span data-ttu-id="32c63-181">Boolean</span><span class="sxs-lookup"><span data-stu-id="32c63-181">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="32c63-182">[Boolean.TrueString](xref:System.Boolean.TrueString) または [Boolean.FalseString](xref:System.Boolean.FalseString) のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-182">Returns either [Boolean.TrueString](xref:System.Boolean.TrueString) or [Boolean.FalseString](xref:System.Boolean.FalseString).</span></span>
[<span data-ttu-id="32c63-183">Byte</span><span class="sxs-lookup"><span data-stu-id="32c63-183">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="32c63-184">`Byte.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Byte](xref:System.Byte) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-184">Calls `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Byte](xref:System.Byte) value for the current culture.</span></span>
[<span data-ttu-id="32c63-185">Char</span><span class="sxs-lookup"><span data-stu-id="32c63-185">Char</span></span>](xref:System.Char) | <span data-ttu-id="32c63-186">文字を文字列として返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-186">Returns the character as a string.</span></span>
[<span data-ttu-id="32c63-187">DateTime</span><span class="sxs-lookup"><span data-stu-id="32c63-187">DateTime</span></span>](xref:System.DateTime) | <span data-ttu-id="32c63-188">`DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて日付と時刻の値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-188">Calls `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` to format the date and time value for the current culture.</span></span> 
[<span data-ttu-id="32c63-189">Decimal</span><span class="sxs-lookup"><span data-stu-id="32c63-189">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="32c63-190">`Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Decimal](xref:System.Decimal) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-190">Calls `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Decimal](xref:System.Decimal) value for the current culture.</span></span>
[<span data-ttu-id="32c63-191">Double</span><span class="sxs-lookup"><span data-stu-id="32c63-191">Double</span></span>](xref:System.Double) | <span data-ttu-id="32c63-192">`Double.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Double](xref:System.Double) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-192">Calls `Double.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Double](xref:System.Double) value for the current culture.</span></span>
[<span data-ttu-id="32c63-193">Int16</span><span class="sxs-lookup"><span data-stu-id="32c63-193">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="32c63-194">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int16](xref:System.Int16) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-194">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int16](xref:System.Int16) value for the current culture.</span></span>
[<span data-ttu-id="32c63-195">Int32</span><span class="sxs-lookup"><span data-stu-id="32c63-195">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="32c63-196">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int32](xref:System.Int32) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-196">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int32](xref:System.Int32) value for the current culture.</span></span>
[<span data-ttu-id="32c63-197">Int64</span><span class="sxs-lookup"><span data-stu-id="32c63-197">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="32c63-198">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int64](xref:System.Int64) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-198">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int64](xref:System.Int64) value for the current culture.</span></span>
[<span data-ttu-id="32c63-199">SByte</span><span class="sxs-lookup"><span data-stu-id="32c63-199">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="32c63-200">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて[SByte](xref:System.SByte) 値の</span><span class="sxs-lookup"><span data-stu-id="32c63-200">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [SByte](xref:System.SByte)</span></span> | <span data-ttu-id="32c63-201">書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-201">value for the current culture.</span></span>
[<span data-ttu-id="32c63-202">Single</span><span class="sxs-lookup"><span data-stu-id="32c63-202">Single</span></span>](xref:System.Single) | <span data-ttu-id="32c63-203">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Single](xref:System.Single) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-203">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Single](xref:System.Single) value for the current culture.</span></span>
[<span data-ttu-id="32c63-204">UInt32</span><span class="sxs-lookup"><span data-stu-id="32c63-204">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="32c63-205">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt32](xref:System.UInt32) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-205">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32)value for the current culture.</span></span>
[<span data-ttu-id="32c63-206">UInt32</span><span class="sxs-lookup"><span data-stu-id="32c63-206">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="32c63-207">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt32](xref:System.UInt32) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-207">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32) value for the current culture.</span></span>
[<span data-ttu-id="32c63-208">UInt64</span><span class="sxs-lookup"><span data-stu-id="32c63-208">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="32c63-209">`Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt64](xref:System.UInt64) 値の書式設定をします。</span><span class="sxs-lookup"><span data-stu-id="32c63-209">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt64](xref:System.UInt64)  value for the current culture.</span></span>

## <a name="the-tostring-method-and-format-strings"></a><span data-ttu-id="32c63-210">ToString メソッドと書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-210">The ToString method and format strings</span></span>

<span data-ttu-id="32c63-211">既定の [ToString](xref:System.Object.ToString) メソッドや [ToString](xref:System.Object.ToString) のオーバーライドの使用は、オブジェクトの文字列形式が 1 つの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-211">Relying on the default [ToString](xref:System.Object.ToString) method or overriding [ToString](xref:System.Object.ToString) is appropriate when an object has a single string representation.</span></span> <span data-ttu-id="32c63-212">しかし、多くの場合オブジェクトの値には複数の形式があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-212">However, the value of an object often has multiple representations.</span></span> <span data-ttu-id="32c63-213">たとえば、温度は華氏、摂氏、またはケルビンで表現できます。</span><span class="sxs-lookup"><span data-stu-id="32c63-213">For example, a temperature can be expressed in degrees Fahrenheit, degrees Celsius, or kelvins.</span></span> <span data-ttu-id="32c63-214">また、整数値 10 は 10、10.0、1.0e01、$10.00 などの多くの方法で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-214">Similarly, the integer value 10 can be represented in numerous ways, including 10, 10.0, 1.0e01, or $10.00.</span></span>

<span data-ttu-id="32c63-215">.NET では、書式指定文字列を使用することで、1 つの値に複数の文字列形式を持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-215">To enable a single value to have multiple string representations, .NET uses format strings.</span></span> <span data-ttu-id="32c63-216">書式指定文字列とは定義済みの書式指定子を 1 つ以上含む文字列です。書式指定子とは、[ToString](xref:System.Object.ToString) メソッドによるその出力の書式設定方法を定義する 1 文字または文字グループです。</span><span class="sxs-lookup"><span data-stu-id="32c63-216">A format string is a string that contains one or more predefined format specifiers, which are single characters or groups of characters that define how the [ToString](xref:System.Object.ToString) method should format its output.</span></span> <span data-ttu-id="32c63-217">書式指定文字列はパラメーターとしてオブジェクトの [ToString](xref:System.Object.ToString) メソッドに渡され、オブジェクトの値の文字列形式の表示方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="32c63-217">The format string is then passed as a parameter to the object's [ToString](xref:System.Object.ToString) method and determines how the string representation of that object's value should appear.</span></span>

<span data-ttu-id="32c63-218">.NET では、すべての数値型、日付/時刻型、および列挙型で、定義済みの一連の書式指定子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="32c63-218">All numeric types, date and time types, and enumeration types in .NET support a predefined set of format specifiers.</span></span> <span data-ttu-id="32c63-219">書式指定文字列を使用して、アプリケーションで定義されたデータ型の文字列形式を複数定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-219">You can also use format strings to define multiple string representations of your application-defined data types.</span></span>

### <a name="standard-format-strings"></a><span data-ttu-id="32c63-220">標準の書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-220">Standard format strings</span></span>

<span data-ttu-id="32c63-221">標準書式指定文字列には、適用先のオブジェクトの文字列形式を定義する英字の単一の書式指定子と、結果文字列に表示される桁数に影響するオプションの精度指定子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="32c63-221">A standard format string contains a single format specifier, which is an alphabetic character that defines the string representation of the object to which it is applied, along with an optional precision specifier that affects how many digits are displayed in the result string.</span></span> <span data-ttu-id="32c63-222">精度指定子が省略されるかサポートされていない場合、標準書式指定子は標準書式指定文字列と同じになります。</span><span class="sxs-lookup"><span data-stu-id="32c63-222">If the precision specifier is omitted or is not supported, a standard format specifier is equivalent to a standard format string.</span></span> 

<span data-ttu-id="32c63-223">.NET では、すべての数値型、すべての日付/時刻型、およびすべての列挙型に対して一連の標準書式指定子が定義されています。</span><span class="sxs-lookup"><span data-stu-id="32c63-223">.NET defines a set of standard format specifiers for all numeric types, all date and time types, and all enumeration types.</span></span> <span data-ttu-id="32c63-224">たとえば、それらのカテゴリごとに、対応する型の値の一般的な文字列形式を定義する "G" 標準書式指定子がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="32c63-224">For example, each of these categories supports a "G" standard format specifier, which defines a general string representation of a value of that type.</span></span>

<span data-ttu-id="32c63-225">列挙型の標準書式指定文字列は、値の文字列形式を直接制御します。</span><span class="sxs-lookup"><span data-stu-id="32c63-225">Standard format strings for enumeration types directly control the string representation of a value.</span></span> <span data-ttu-id="32c63-226">列挙値の [ToString](xref:System.Object.ToString) メソッドに渡された書式指定文字列によって、文字列名 ("G" 書式指定子および "F" 書式指定子)、基になる整数値 ("D" 書式指定子)、または 16 進値 ("X" 書式指定子) のどの形式で値を表示するかが決定します。</span><span class="sxs-lookup"><span data-stu-id="32c63-226">The format strings passed to an enumeration value’s [ToString](xref:System.Object.ToString) method determine whether the value is displayed using its string name (the "G" and "F" format specifiers), its underlying integral value (the "D" format specifier), or its hexadecimal value (the "X" format specifier).</span></span> <span data-ttu-id="32c63-227">次のコード例では、標準書式指定文字列を使用して、[DayOfWeek](xref:System.DayOfWeek) 列挙値の書式を設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-227">The following example illustrates the use of standard format strings to format a [DayOfWeek](xref:System.DayOfWeek) enumeration value.</span></span> 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

<span data-ttu-id="32c63-228">列挙型書式指定文字列については、「[列挙型書式指定文字列](enumeration-format.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-228">For information about enumeration format strings, see [Enumeration format strings](enumeration-format.md).</span></span>

<span data-ttu-id="32c63-229">数値型の標準書式指定文字列は、通常、表示される桁数が 1 つ以上のプロパティ値によって制御される結果文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-229">Standard format strings for numeric types usually define a result string whose precise appearance is controlled by one or more property values.</span></span> <span data-ttu-id="32c63-230">たとえば、"C" 書式指定子は数字を通貨値として書式設定します。</span><span class="sxs-lookup"><span data-stu-id="32c63-230">For example, the "C" format specifier formats a number as a currency value.</span></span> <span data-ttu-id="32c63-231">唯一のパラメーターとして "C" 書式指定子を渡して [ToString](xref:System.Object.ToString) メソッドを呼び出した場合、現在のカルチャの [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの次のプロパティ値を使用して数値の文字列形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-231">When you call the [ToString](xref:System.Object.ToString) method with the "C" format specifier as the only parameter, the following property values from the current culture’s [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object are used to define the string representation of the numeric value:</span></span>

* <span data-ttu-id="32c63-232">[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) プロパティ。現在のカルチャの通貨記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="32c63-232">The [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property, which specifies the current culture’s currency symbol.</span></span>

* <span data-ttu-id="32c63-233">[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) プロパティまたは [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) プロパティ。次の情報を特定する整数を返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-233">The [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) or [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) property, which returns an integer that determines the following:</span></span> 

    * <span data-ttu-id="32c63-234">通貨記号の位置。</span><span class="sxs-lookup"><span data-stu-id="32c63-234">The placement of the currency symbol.</span></span>
    
    * <span data-ttu-id="32c63-235">負の値を表すために、先頭の負の符号、末尾の負の符号、またはかっこのどれを使用するか。</span><span class="sxs-lookup"><span data-stu-id="32c63-235">Whether negative values are indicated by a leading negative sign, a trailing negative sign, or parentheses.</span></span>
    
    * <span data-ttu-id="32c63-236">数値と通貨記号の間にスペース文字を表示するかどうか。</span><span class="sxs-lookup"><span data-stu-id="32c63-236">Whether a space appears between the numeric value and the currency symbol.</span></span>
    
* <span data-ttu-id="32c63-237">[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) プロパティ。結果文字列の小数点以下の桁数を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-237">The [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) property, which defines the number of fractional digits in the result string.</span></span>

* <span data-ttu-id="32c63-238">[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) プロパティ。結果文字列の小数点の記号を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-238">The [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property, which defines the decimal separator symbol in the result string.</span></span>

* <span data-ttu-id="32c63-239">[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) プロパティ。桁区切り記号を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-239">The [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property, which defines the group separator symbol.</span></span>

* <span data-ttu-id="32c63-240">[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) プロパティ。整数部の各グループの桁数を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-240">The [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) property, which defines the number of digits in each group to the left of the decimal.</span></span>

* <span data-ttu-id="32c63-241">[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) プロパティ。かっこを使用せずに負の値を表す場合に結果文字列で使用する負の符号を決定します。</span><span class="sxs-lookup"><span data-stu-id="32c63-241">The [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) property, which determines the negative sign used in the result string if parentheses are not used to indicate negative values.</span></span>

<span data-ttu-id="32c63-242">さらに、数値書式指定文字列には、精度指定子が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-242">In addition, numeric format strings may include a precision specifier.</span></span> <span data-ttu-id="32c63-243">この指定子の意味は一緒に使用される書式指定文字列によって異なりますが、通常は、結果文字列に表示される合計桁数か小数点以下の桁数を示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-243">The meaning of this specifier depends on the format string with which it is used, but it typically indicates either the total number of digits or the number of fractional digits that should appear in the result string.</span></span> <span data-ttu-id="32c63-244">たとえば、次の例では、"X4" の標準数値文字列と精度指定子を使用して、4 桁の 16 進数から成る文字列値を作成します。</span><span class="sxs-lookup"><span data-stu-id="32c63-244">For example, the following example uses the "X4" standard numeric string and a precision specifier to create a string value that has four hexadecimal digits.</span></span>

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

<span data-ttu-id="32c63-245">標準の数値書式指定文字列の詳細については、「[標準の数値書式指定文字列](standard-numeric.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-245">For more information about standard numeric formatting strings, see [Standard numeric format strings](standard-numeric.md).</span></span> 

<span data-ttu-id="32c63-246">日付と時刻の値の標準書式指定文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) クラスに格納されているカスタム書式指定文字列のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="32c63-246">Standard format strings for date and time values are aliases for custom format strings stored by a particular [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) class.</span></span> <span data-ttu-id="32c63-247">たとえば、"D" 書式指定子を渡して日付と時刻の値の [ToString](xref:System.Object.ToString) メソッドを呼び出すと、現在のカルチャの [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) プロパティに格納されているカスタム書式指定文字列を使用して日付と時刻が表示されます</span><span class="sxs-lookup"><span data-stu-id="32c63-247">For example, calling the [ToString](xref:System.Object.ToString) method of a date and time value with the "D" format specifier displays the date and time by using the custom format string stored in the current culture’s [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) property.</span></span> <span data-ttu-id="32c63-248">(カスタム書式指定文字列の詳細については、「[カスタム書式指定文字列](#custom-format-strings)」のセクションを参照してください)。この関係を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-248">(For more information about custom format strings, see the [Custom format strings](#custom-format-strings) section.) The following example illustrates this relationship.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

<span data-ttu-id="32c63-249">標準の日時書式指定文字列の詳細については、「[標準の日時書式指定文字列](standard-datetime.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-249">For more information about standard date and time format strings, see [Standard date and time format strings](standard-datetime.md).</span></span>

<span data-ttu-id="32c63-250">また、標準書式指定文字列を使用して、オブジェクトの `ToString(String)` メソッドによって生成された、アプリケーション定義のオブジェクトの文字列形式を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-250">You can also use standard format strings to define the string representation of an application-defined object that is produced by the object’s `ToString(String)` method.</span></span> <span data-ttu-id="32c63-251">オブジェクトでサポートする特定の標準書式指定子を定義したり、それらで大文字と小文字を区別するかしないかを決定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-251">You can define the specific standard format specifiers that your object supports, and you can determine whether they are case-sensitive or case-insensitive.</span></span> <span data-ttu-id="32c63-252">`ToString(String)` メソッドの実装で、以下がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="32c63-252">Your implementation of the `ToString(String)` method should support the following:</span></span>

* <span data-ttu-id="32c63-253">オブジェクトの一般的な書式または共通の書式を表す "G" 書式指定子。</span><span class="sxs-lookup"><span data-stu-id="32c63-253">A "G" format specifier that represents a customary or common format of the object.</span></span> <span data-ttu-id="32c63-254">オブジェクトの `ToString` メソッドのパラメーターなしのオーバーロードで、その `ToString(String)` オーバーロードを呼び出し、それに "G" 標準書式指定文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="32c63-254">The parameterless overload of your object's `ToString` method should call its `ToString(String)` overload and pass it the "G" standard format string.</span></span>

* <span data-ttu-id="32c63-255">null 参照に相当する書式指定子。</span><span class="sxs-lookup"><span data-stu-id="32c63-255">Support for a format specifier that is equal to a null reference.</span></span> <span data-ttu-id="32c63-256">null 参照に相当する書式指定子は "G" 書式指定子と同等に扱う必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-256">A format specifier that is equal to a null reference should be considered equivalent to the "G" format specifier.</span></span>

<span data-ttu-id="32c63-257">たとえば、`Temperature` クラスの場合、内部的には温度を摂氏で格納し、書式指定子を使用して `Temperature` オブジェクトの値を摂氏、華氏、およびケルビンで表すことができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-257">For example, a `Temperature` class can internally store the temperature in degrees Celsius and use format specifiers to represent the value of the `Temperature` object in degrees Celsius, degrees Fahrenheit, and kelvins.</span></span> <span data-ttu-id="32c63-258">具体的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-258">The following example provides an illustration.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a><span data-ttu-id="32c63-259">カスタム書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-259">Custom format strings</span></span>

<span data-ttu-id="32c63-260">.NET では、標準書式指定文字列のほかに、数値および日付と時刻の値の両方のカスタム書式指定文字列が定義されています。</span><span class="sxs-lookup"><span data-stu-id="32c63-260">In addition to the standard format strings, .NET defines custom format strings for both numeric values and date and time values.</span></span> <span data-ttu-id="32c63-261">カスタム書式指定文字列は、値の文字列形式を定義する 1 つ以上のカスタム書式指定子で構成されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-261">A custom format string consists of one or more custom format specifiers that define the string representation of a value.</span></span> <span data-ttu-id="32c63-262">たとえば、"yyyy/mm/dd hh:mm:ss.ffff t zzz" というカスタム日時書式指定文字列の場合、en-US カルチャでは日付が "2008/11/15 07:45:00.0000 P -08:00" という文字列形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-262">For example, the custom date and time format string "yyyy/mm/dd hh:mm:ss.ffff t zzz" converts a date to its string representation in the form "2008/11/15 07:45:00.0000 P -08:00" for the en-US culture.</span></span> <span data-ttu-id="32c63-263">また、"0000" というカスタム書式指定文字列の場合、整数値 12 は "0012" に変換されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-263">Similarly, the custom format string "0000" converts the integer value 12 to "0012".</span></span> <span data-ttu-id="32c63-264">カスタム書式指定文字列の一覧については、「[カスタム日時書式指定文字列](custom-datetime.md)」および「[カスタム数値書式指定文字列](custom-numeric.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-264">For a complete list of custom format strings, see [Custom date and time format strings](custom-datetime.md) and [Custom numeric format strings](custom-numeric.md).</span></span>

<span data-ttu-id="32c63-265">書式指定文字列が単一のカスタム書式指定子で構成される場合は、標準書式指定子と混同しないように、書式指定子の前にパーセント (%) 記号を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-265">If a format string consists of a single custom format specifier, the format specifier should be preceded by the percent (%) symbol to avoid confusion with a standard format specifier.</span></span> <span data-ttu-id="32c63-266">次の例では、"M" カスタム書式指定子を使用して、特定の日付の月を表す 1 桁または 2 桁の数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-266">The following example uses the "M" custom format specifier to display a one-digit or two-digit number of the month of a particular date.</span></span>

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

<span data-ttu-id="32c63-267">日付および時刻の値の標準書式指定文字列の多くは、[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティによって定義されているカスタム書式指定文字列のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="32c63-267">Many standard format strings for date and time values are aliases for custom format strings that are defined by properties of the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> <span data-ttu-id="32c63-268">また、カスタム書式指定文字列を使用することで、数値または日付と時刻の値に対して、柔軟にアプリケーション定義の書式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="32c63-268">Custom format strings also offer considerable flexibility in providing application-defined formatting for numeric values or date and time values.</span></span> <span data-ttu-id="32c63-269">複数のカスタム書式指定子を 1 つのカスタム書式指定文字列に結合することによって、数値および日付と時刻の値の両方に対するカスタムの結果文字列を独自に定義することができます。</span><span class="sxs-lookup"><span data-stu-id="32c63-269">You can define your own custom result strings for both numeric values and date and time values by combining multiple custom format specifiers into a single custom format string.</span></span> <span data-ttu-id="32c63-270">次の例では、月の名前、日付、および年の後に、かっこで囲んで曜日を表示するカスタム書式指定文字列を定義しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-270">The following example defines a custom format string that displays the day of the week in parentheses after the month name, day, and year.</span></span>

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

<span data-ttu-id="32c63-271">次の例では、[Int64](xref:System.Int64) 値を米国で標準的な 7 桁の電話番号を市外局番と共に表示するカスタム書式指定文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="32c63-271">The following example defines a custom format string that displays an [Int64](xref:System.Int64) value as a standard, seven-digit U.S. telephone number along with its area code.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

<span data-ttu-id="32c63-272">一般には、アプリケーション定義の型に対する書式設定のほとんどのニーズに標準書式指定文字列を使用して対応できますが、カスタム書式指定子を定義して型の書式を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-272">Although standard format strings can generally handle most of the formatting needs for your application-defined types, you may also define custom format specifiers to format your types.</span></span> 

### <a name="format-strings-and-net-types"></a><span data-ttu-id="32c63-273">書式指定文字列と .NET 型</span><span class="sxs-lookup"><span data-stu-id="32c63-273">Format strings and .NET types</span></span>

<span data-ttu-id="32c63-274">すべての数値型 (つまり、[Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)、[BigInteger](xref:System.Numerics.BigInteger) 型)、および [DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)、[TimeSpan](xref:System.TimeSpan)、[Guid](xref:System.Guid) と、すべての列挙型が書式指定文字列による書式設定に対応しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-274">All numeric types (that is, the [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64), and [BigInteger](xref:System.Numerics.BigInteger) types), as well as the [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid), and all enumeration types, support formatting with format strings.</span></span> <span data-ttu-id="32c63-275">各型でサポートされている特定の書式指定文字列については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-275">For information on the specific format strings supported by each type, see the following topics:</span></span> 

<span data-ttu-id="32c63-276">タイトル</span><span class="sxs-lookup"><span data-stu-id="32c63-276">Title</span></span> | <span data-ttu-id="32c63-277">定義</span><span class="sxs-lookup"><span data-stu-id="32c63-277">Definition</span></span>
----- | ----------
[<span data-ttu-id="32c63-278">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-278">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="32c63-279">数値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-279">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="32c63-280">カスタム数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-280">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="32c63-281">数値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-281">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="32c63-282">標準の日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-282">Standard date and time format strings</span></span>](standard-datetime.md) | <span data-ttu-id="32c63-283">[DateTime](xref:System.DateTime) 値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-283">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="32c63-284">カスタム日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-284">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="32c63-285">[DateTime](xref:System.DateTime) 値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-285">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="32c63-286">標準 TimeSpan 書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-286">Standard TimeSpan format Strings</span></span>](standard-timespan.md) | <span data-ttu-id="32c63-287">時間間隔に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-287">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="32c63-288">カスタム TimeSpan 書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-288">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="32c63-289">時間間隔に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-289">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="32c63-290">列挙型書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-290">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="32c63-291">列挙型の文字列形式を作成するために使用される標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-291">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
<span data-ttu-id="32c63-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span><span class="sxs-lookup"><span data-stu-id="32c63-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span></span> | <span data-ttu-id="32c63-293">[Guid](xref:System.Guid) 値の標準的書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-293">Describes standard format strings for [Guid](xref:System.Guid) values.</span></span>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a><span data-ttu-id="32c63-294">書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定</span><span class="sxs-lookup"><span data-stu-id="32c63-294">Culture-Sensitive Formatting with Format Providers and the IFormatProvider Interface</span></span>

<span data-ttu-id="32c63-295">書式指定子を利用することでオブジェクトの書式をカスタマイズできますが、多くの場合、意味のあるオブジェクトの文字列形式を生成するには追加の書式設定情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="32c63-295">Although format specifiers let you customize the formatting of objects, producing a meaningful string representation of objects often requires additional formatting information.</span></span> <span data-ttu-id="32c63-296">たとえば、"C" 標準書式指定文字列または "$ #,#.00" などのカスタム書式指定文字列を使用して数字を通貨値として書式設定する場合、少なくとも、正しい通貨記号、桁区切り記号、および小数点記号についての情報を書式設定された文字列に含めることができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-296">For example, formatting a number as a currency value by using either the "C" standard format string or a custom format string such as "$ #,#.00" requires, at a minimum, information about the correct currency symbol, group separator, and decimal separator to be available to include in the formatted string.</span></span> <span data-ttu-id="32c63-297">.NET では、[IFormatProvider](xref:System.IFormatProvider) インターフェイスによって、この追加の書式設定情報を利用できるようにします。このインターフェイスは、数値型および日付/時刻型の `ToString` メソッドの 1 つ以上のオーバーロードに対するパラメーターとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-297">In .NET, this additional formatting information is made available through the [IFormatProvider](xref:System.IFormatProvider) interface, which is provided as a parameter to one or more overloads of the `ToString` method of numeric types and date and time types.</span></span> <span data-ttu-id="32c63-298">[IFormatProvider](xref:System.IFormatProvider) の実装は .NET で使用され、カルチャ固有の書式指定をサポートします。</span><span class="sxs-lookup"><span data-stu-id="32c63-298">[IFormatProvider](xref:System.IFormatProvider) implementations are used in .NET to support culture-specific formatting.</span></span> <span data-ttu-id="32c63-299">それぞれ異なるカルチャを示す 3 つの [IFormatProvider](xref:System.IFormatProvider) オブジェクトを使用してオブジェクトの書式を設定した場合に、その文字列形式がどのように変化するかを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-299">The following example illustrates how the string representation of an object changes when it is formatted with three [IFormatProvider](xref:System.IFormatProvider) objects that represent different cultures.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

<span data-ttu-id="32c63-300">[IFormatProvider](xref:System.IFormatProvider) インターフェイスには、[GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)) という 1 つのメソッドが含まれています。このメソッドには、書式設定情報を提供するオブジェクトの型を指定する 1 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="32c63-300">The [IFormatProvider](xref:System.IFormatProvider) interface includes one method, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), which has a single parameter that specifies the type of object that provides formatting information.</span></span> <span data-ttu-id="32c63-301">このメソッドがその型のオブジェクトを提供できる場合は、それが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-301">If the method can provide an object of that type, it returns it.</span></span> <span data-ttu-id="32c63-302">それ以外の場合は、null 参照を返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-302">Otherwise, it returns a null reference.</span></span>

<span data-ttu-id="32c63-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) はコールバック メソッドです。</span><span class="sxs-lookup"><span data-stu-id="32c63-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) is a callback method.</span></span> <span data-ttu-id="32c63-304">[IFormatProvider](xref:System.IFormatProvider) パラメーターを含む `ToString` メソッド オーバーロードを呼び出すと、その [IFormatProvider](xref:System.IFormatProvider) オブジェクトの [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-304">When you call a `ToString` method overload that includes an [IFormatProvider](xref:System.IFormatProvider) parameter, it calls the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method of that [IFormatProvider](xref:System.IFormatProvider) object.</span></span> <span data-ttu-id="32c63-305">[GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドは、*formatType* パラメーターで指定された、必要な書式設定情報を提供するオブジェクトを `ToString` メソッドに返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-305">The [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method is responsible for returning an object that provides the necessary formatting information, as specified by its *formatType* parameter, to the `ToString` method.</span></span> 

<span data-ttu-id="32c63-306">数多くの書式指定メソッドや文字列変換メソッドに [IFormatProvider](xref:System.IFormatProvider) 型のパラメーターが含まれていますが、多くの場合、メソッドを呼び出すときはパラメーターの値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-306">A number of formatting or string conversion methods include a parameter of type [IFormatProvider](xref:System.IFormatProvider), but in many cases the value of the parameter is ignored when the method is called.</span></span> <span data-ttu-id="32c63-307">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドに渡される [Type](xref:System.Type) オブジェクトのパラメーターと型を使用する書式指定メソッドの一部を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-307">The following table lists some of the formatting methods that use the parameter and the type of the [Type](xref:System.Type) object that they pass to the [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method.</span></span> 

<span data-ttu-id="32c63-308">メソッド</span><span class="sxs-lookup"><span data-stu-id="32c63-308">Method</span></span> | <span data-ttu-id="32c63-309">*formatType* パラメーターの型</span><span class="sxs-lookup"><span data-stu-id="32c63-309">Type of *formatType* parameter</span></span>
------ | ------------------------------
<span data-ttu-id="32c63-310">数値型の `ToString` メソッド</span><span class="sxs-lookup"><span data-stu-id="32c63-310">`ToString` method of numeric types</span></span> | [<span data-ttu-id="32c63-311">System.Globalization.NumberFormatInfo</span><span class="sxs-lookup"><span data-stu-id="32c63-311">System.Globalization.NumberFormatInfo</span></span>](xref:System.Globalization.NumberFormatInfo)
<span data-ttu-id="32c63-312">日付/時刻型の `ToString` メソッド</span><span class="sxs-lookup"><span data-stu-id="32c63-312">`ToString` method of date and time types</span></span> | [<span data-ttu-id="32c63-313">System.Globalization.DateTimeFormatInfo</span><span class="sxs-lookup"><span data-stu-id="32c63-313">System.Globalization.DateTimeFormatInfo</span></span>](xref:System.Globalization.DateTimeFormatInfo)
<span data-ttu-id="32c63-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="32c63-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="32c63-315">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="32c63-315">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)
<span data-ttu-id="32c63-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="32c63-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="32c63-317">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="32c63-317">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

<span data-ttu-id="32c63-318">.NET には、[IFormatProvider](xref:System.IFormatProvider) を実装する次の 3 つのクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="32c63-318">.NET provides three classes that implement [IFormatProvider](xref:System.IFormatProvider):</span></span> 

* <span data-ttu-id="32c63-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)。このクラスは、特定のカルチャの日付と時刻の値に対する書式設定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="32c63-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), a class that provides formatting information for date and time values for a specific culture.</span></span> <span data-ttu-id="32c63-320">対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、それ自身のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-320">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="32c63-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)。このクラスは、特定のカルチャの数値に対する書式設定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="32c63-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a class that provides numeric formatting information for a specific culture.</span></span> <span data-ttu-id="32c63-322">対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、それ自身のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-322">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="32c63-323">[CultureInfo](xref:System.Globalization.CultureInfo)。</span><span class="sxs-lookup"><span data-stu-id="32c63-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span></span> <span data-ttu-id="32c63-324">対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、数値に対する書式設定情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトか、日付と時刻の値に対する書式設定情報を提供する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのいずれかが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-324">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation can return either a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to provide numeric formatting information or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object to provide formatting information for date and time values.</span></span> 

<span data-ttu-id="32c63-325">また、これらのクラスのうちのいずれかを置き換える独自の書式プロバイダーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="32c63-325">You can also implement your own format provider to replace any one of these classes.</span></span> <span data-ttu-id="32c63-326">ただし、実装の `GetFormat` メソッドは、書式設定情報を `ToString` メソッドに渡す場合、前の表に示した型のオブジェクトを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-326">However, your implementation’s `GetFormat` method must return an object of the type listed in the previous table if it has to provide formatting information to the `ToString` method.</span></span>

### <a name="culture-sensitive-formatting-of-numeric-values"></a><span data-ttu-id="32c63-327">数値のカルチャに依存した書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-327">Culture-sensitive formatting of numeric values</span></span>

<span data-ttu-id="32c63-328">既定では、数値の書式指定はカルチャに依存します。</span><span class="sxs-lookup"><span data-stu-id="32c63-328">By default, the formatting of numeric values is culture-sensitive.</span></span> <span data-ttu-id="32c63-329">書式指定メソッドを呼び出すときにカルチャを指定しない場合は、現在のスレッド カルチャの書式指定規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-329">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="32c63-330">次に示す例では、現在のスレッド カルチャを 4 回変更した後に、[Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32c63-330">This is illustrated in the following example, which changes the current thread culture four times and then calls the [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) method.</span></span> <span data-ttu-id="32c63-331">各ケースでは、結果の文字列は、現在のカルチャの書式指定規則を反映します。</span><span class="sxs-lookup"><span data-stu-id="32c63-331">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="32c63-332">これは、各数値型の `ToString` メソッドへの呼び出しを、`ToString(String)` メソッドと `ToString(String, IFormatProvider)` メソッドがラップするためです。</span><span class="sxs-lookup"><span data-stu-id="32c63-332">This is because the `ToString` and `ToString(String)` methods wrap calls to each numeric type's `ToString(String, IFormatProvider)` method.</span></span> 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

<span data-ttu-id="32c63-333">また、*provider* パラメーターを持つ `ToString` オーバーロードを呼び出して、次のどちらかを渡すことにより、特定カルチャの数値を書式指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-333">You can also format a numeric value for a specific culture by calling a `ToString` overload that has a *provider* parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="32c63-334">使用される書式指定規則のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="32c63-334">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="32c63-335">その [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドは、[CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) プロパティの値を返します。このプロパティは、数値にカルチャ固有の書式指定情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="32c63-335">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="32c63-336">使用されるカルチャ固有の書式指定規則を定義する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="32c63-336">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="32c63-337">その [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) メソッドでは、それ自身のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-337">Its [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="32c63-338">次の例では、浮動小数点数を書式指定する際に、英語 (米国) と英語 (英国) のカルチャおよびフランス語とロシア語のニュートラル カルチャを表す [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="32c63-338">The following example uses [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a floating-point number.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a><span data-ttu-id="32c63-339">日付と時刻の値のカルチャに依存した書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-339">Culture-sensitive formatting of date and time values</span></span>

<span data-ttu-id="32c63-340">既定では、日時の値の書式指定はカルチャに依存します。</span><span class="sxs-lookup"><span data-stu-id="32c63-340">By default, the formatting of date and time values is culture-sensitive.</span></span> <span data-ttu-id="32c63-341">書式指定メソッドを呼び出すときにカルチャを指定しない場合は、現在のスレッド カルチャの書式指定規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-341">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="32c63-342">次に示す例では、現在のスレッド カルチャを 4 回変更した後に、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32c63-342">This is illustrated in the following example, which changes the current thread culture four times and then calls the [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) method.</span></span> <span data-ttu-id="32c63-343">各ケースでは、結果の文字列は、現在のカルチャの書式指定規則を反映します。</span><span class="sxs-lookup"><span data-stu-id="32c63-343">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="32c63-344">これは、[DateTime.ToString()](xref:System.DateTime.ToString)、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String))、[DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String))、[DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) の各メソッドが、[DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) メソッドおよび [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) メソッドへの呼び出しをラップするためです。</span><span class="sxs-lookup"><span data-stu-id="32c63-344">This is because the [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)), and [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) methods wrap calls to the [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) methods.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

<span data-ttu-id="32c63-345">provider パラメーターを持つ [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) または [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) オーバーロードを呼び出して、次のどちらかを渡すことにより、特定カルチャの日時の値を書式指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-345">You can also format a date and time value for a specific culture by calling a [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) overload that has a provider parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="32c63-346">使用される書式指定規則のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="32c63-346">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="32c63-347">その [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドは、[CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) プロパティの値を返します。このプロパティは、数値にカルチャ固有の書式指定情報を提供する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="32c63-347">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="32c63-348">使用されるカルチャ固有の書式指定規則を定義する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="32c63-348">A [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="32c63-349">その [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) メソッドでは、それ自身のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-349">Its [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="32c63-350">次の例では、日付を書式指定する際に、英語 (米国) と英語 (英国) のカルチャおよびフランス語とロシア語のニュートラル カルチャを表す [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="32c63-350">The following example uses [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a date.</span></span> 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a><span data-ttu-id="32c63-351">IFormattable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32c63-351">The IFormattable interface</span></span>

<span data-ttu-id="32c63-352">通常、書式指定文字列および [IFormatProvider](xref:System.IFormatProvider) パラメーターを使用して `ToString` メソッドをオーバーロードする型は、[IFormattable](xref:System.IFormattable) インターフェイスも実装します。</span><span class="sxs-lookup"><span data-stu-id="32c63-352">Typically, types that overload the `ToString` method with a format string and an [IFormatProvider](xref:System.IFormatProvider) parameter also implement the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="32c63-353">このインターフェイスには、[IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) という単一のメンバーがあります。このメンバーには、パラメーターとして書式指定文字列と書式プロバイダーの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="32c63-353">This interface has a single member, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), that includes both a format string and a format provider as parameters.</span></span>

<span data-ttu-id="32c63-354">アプリケーション定義のクラスに [IFormattable](xref:System.IFormattable) インターフェイスを実装した場合、2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="32c63-354">Implementing the [IFormattable](xref:System.IFormattable) interface for your application-defined class offers two advantages:</span></span> 

* <span data-ttu-id="32c63-355">[Convert](xref:System.Convert) クラスによる文字列変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="32c63-355">Support for string conversion by the [Convert](xref:System.Convert) class.</span></span> <span data-ttu-id="32c63-356">[Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) メソッドおよび [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) メソッドを呼び出すと、自動的に [IFormattable](xref:System.IFormattable) の実装が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-356">Calls to the [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) and [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) methods call your [IFormattable](xref:System.IFormattable) implementation automatically.</span></span>

* <span data-ttu-id="32c63-357">複合書式指定がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="32c63-357">Support for composite formatting.</span></span> <span data-ttu-id="32c63-358">書式指定文字列を含む書式指定項目を使用してカスタムの型の書式を設定する場合に、共通言語ランタイムによって自動的に [IFormattable](xref:System.IFormattable) の実装が呼び出され、それに書式指定文字列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-358">If a format item that includes a format string is used to format your custom type, the Common Language Runtime automatically calls your [IFormattable](xref:System.IFormattable) implementation and passes it the format string.</span></span> <span data-ttu-id="32c63-359">`String.Format` メソッドや `Console.WriteLine` メソッドを使用した複合書式指定の詳細については、「[複合書式指定](#composite-formatting)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-359">For more information about composite formatting with methods such as `String.Format` or `Console.WriteLine`, see the [Composite formatting](#composite-formatting) section.</span></span>

<span data-ttu-id="32c63-360">次の例では、[IFormattable](xref:System.IFormattable) インターフェイスを実装する `Temperature` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-360">The following example defines a `Temperature` class that implements the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="32c63-361">このクラスでは、温度を摂氏で表示するために "C" 書式指定子または "G" 書式指定子、華氏で表示するために "F" 書式指定子、ケルビンで表示するために "K" 書式指定子をそれぞれサポートしています。</span><span class="sxs-lookup"><span data-stu-id="32c63-361">It supports the "C" or "G" format specifiers to display the temperature in Celsius, the "F" format specifier to display the temperature in Fahrenheit, and the "K" format specifier to display the temperature in Kelvin.</span></span>

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

<span data-ttu-id="32c63-362">次の例では、`Temperature` オブジェクトをインスタンス化しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-362">The following example instantiates a `Temperature` object.</span></span> <span data-ttu-id="32c63-363">その後、[ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) メソッドを呼び出し、いくつかの複合書式指定文字列を使用して `Temperature` オブジェクトのさまざまな文字列形式を取得します。</span><span class="sxs-lookup"><span data-stu-id="32c63-363">It then calls the [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) method and uses several composite format strings to obtain different string representations of a `Temperature` object.</span></span> <span data-ttu-id="32c63-364">さらに、それらの各メソッド呼び出しで、`Temperature` クラスの [IFormattable](xref:System.IFormattable) 実装を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-364">Each of these method calls, in turn, calls the [IFormattable](xref:System.IFormattable) implementation of the `Temperature` class.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a><span data-ttu-id="32c63-365">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="32c63-365">Composite formatting</span></span>

<span data-ttu-id="32c63-366">`String.Format` や `StringBuilder.AppendFormat` などの一部のメソッドでは、複合書式指定がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="32c63-366">Some methods, such as `String.Format` and `StringBuilder.AppendFormat`, support composite formatting.</span></span> <span data-ttu-id="32c63-367">複合書式指定文字列は一種のテンプレートで、0 個以上のオブジェクトの文字列形式が組み込まれた単一の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-367">A composite format string is a kind of template that returns a single string that incorporates the string representation of zero, one, or more objects.</span></span> <span data-ttu-id="32c63-368">各オブジェクトは、インデックス付きの書式指定項目によって、複合書式指定文字列で表現されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-368">Each object is represented in the composite format string by an indexed format item.</span></span> <span data-ttu-id="32c63-369">書式指定項目のインデックスは、それが表すオブジェクトのメソッドのパラメーター リスト内の位置と対応しています。</span><span class="sxs-lookup"><span data-stu-id="32c63-369">The index of the format item corresponds to the position of the object that it represents in the method's parameter list.</span></span> <span data-ttu-id="32c63-370">インデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="32c63-370">Indexes are zero-based.</span></span> <span data-ttu-id="32c63-371">たとえば、`String.Format` メソッドの次のメソッド呼び出しでは、最初の書式指定項目 `{0:D}` は `thatDate` の文字列形式に、2 番目の書式指定項目 `{1}` は `item1` の文字列形式に、3 番目の書式指定項目 `{2:C2}` は `item1.Value` の文字列形式に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="32c63-371">For example, in the following call to the `String.Format` method, the first format item, `{0:D}`, is replaced by the string representation of `thatDate`; the second format item, `{1}`, is replaced by the string representation of `item1`; and the third format item, `{2:C2}`, is replaced by the string representation of `item1.Value`.</span></span>

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

<span data-ttu-id="32c63-372">書式項目をそれに対応するオブジェクトの文字列形式に置換することに加えて、書式項目は以下を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-372">In addition to replacing a format item with the string representation of its corresponding object, format items also let you control the following:</span></span> 

* <span data-ttu-id="32c63-373">オブジェクトを文字列として表現する特定の方法 (オブジェクトが [IFormattable](xref:System.IFormattable) インターフェイスを実装し、書式文字列をサポートする場合)。</span><span class="sxs-lookup"><span data-stu-id="32c63-373">The specific way in which an object is represented as a string, if the object implements the [IFormattable](xref:System.IFormattable) interface and supports format strings.</span></span> <span data-ttu-id="32c63-374">これは、: (コロン) 付きの書式項目のインデックスに、有効な書式文字列を続けることによります。</span><span class="sxs-lookup"><span data-stu-id="32c63-374">You do this by following the format item's index with a : (colon) followed by a valid format string.</span></span> <span data-ttu-id="32c63-375">前の例では、日付の値を "d" (短い日付のパターン) 書式文字列 (`{0:d}` など) を書式設定し、数値を "C2" 書式文字列 (`{2:C2}` など) で書式設定して数値を 2 桁の小数部を含む 10 進数を持つ通貨値で表していました。</span><span class="sxs-lookup"><span data-stu-id="32c63-375">The previous example did this by formatting a date value with the "d" (short date pattern) format string (for example, `{0:d}`) and by formatting a numeric value with the "C2" format string (for example, `{2:C2}` to represent the number as a currency value with two fractional decimal digits).</span></span> 

* <span data-ttu-id="32c63-376">オブジェクトの文字列形式を含むフィールドの幅、およびそのフィールドの文字列形式の配置。</span><span class="sxs-lookup"><span data-stu-id="32c63-376">The width of the field that contains the object's string representation, and the alignment of the string representation in that field.</span></span> <span data-ttu-id="32c63-377">これは、, (コンマ) 付きの書式項目のインデックスに、フィールドの幅を続けることによります。</span><span class="sxs-lookup"><span data-stu-id="32c63-377">You do this by following the format item's index with a , (comma) followed the field width.</span></span> <span data-ttu-id="32c63-378">フィールドの幅が正の値の場合、文字列はフィールドで右揃えにし、フィールドの幅が負の値の場合、左揃えにします。</span><span class="sxs-lookup"><span data-stu-id="32c63-378">The string is right-aligned in the field if the field width is a positive value, and it is left-aligned if the field width is a negative value.</span></span> <span data-ttu-id="32c63-379">次の例では、20 文字のフィールドで日付の値を左揃えにし、11 文字のフィールドで、1 桁の小数部を含む 10 進数値を右揃えにします。</span><span class="sxs-lookup"><span data-stu-id="32c63-379">The following example left-aligns date values in a 20-character field, and it right-aligns decimal values with one fractional digit in an 11-character field.</span></span> 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

<span data-ttu-id="32c63-380">配置文字列コンポーネントと書式文字列コンポーネントの両方が存在する場合、前者は後者の前にきます (たとえば `{0,-20:g}`)。</span><span class="sxs-lookup"><span data-stu-id="32c63-380">Note that, if both the alignment string component and the format string component are present, the former precedes the latter (for example, `{0,-20:g}`.</span></span> 

<span data-ttu-id="32c63-381">複合書式指定の詳細については、「[複合書式指定](composite-format.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-381">For more information about composite formatting, see [Composite formatting](composite-format.md).</span></span>

## <a name="custom-formatting-with-icustomformatter"></a><span data-ttu-id="32c63-382">ICustomFormatter を使用したカスタム書式設定</span><span class="sxs-lookup"><span data-stu-id="32c63-382">Custom formatting with ICustomFormatter</span></span>

<span data-ttu-id="32c63-383">[String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) および [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) の 2 つの複合書式指定メソッドには、カスタム書式設定をサポートしている書式プロバイダー パラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="32c63-383">Two composite formatting methods, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) and [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), include a format provider parameter that supports custom formatting.</span></span> <span data-ttu-id="32c63-384">これらの書式指定メソッドのいずれかを呼び出すと、書式プロバイダーの `GetFormat` メソッドに [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを表す [Type](xref:System.Type) オブジェクトが渡されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-384">When either of these formatting methods is called, it passes a [Type](xref:System.Type) object that represents an [ICustomFormatter](xref:System.ICustomFormatter) interface to the format provider’s `GetFormat` method.</span></span> <span data-ttu-id="32c63-385">次に、`GetFormat` メソッドによって、カスタム書式設定を提供する [ICustomFormatter](xref:System.ICustomFormatter) の実装が返されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-385">The `GetFormat` method is then responsible for returning the [ICustomFormatter](xref:System.ICustomFormatter) implementation that provides custom formatting.</span></span>

<span data-ttu-id="32c63-386">[ICustomFormatter](xref:System.ICustomFormatter) インターフェイスには、[Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) という単一のメソッドがあります。このメソッドは、複合書式指定文字列の書式指定項目ごとに 1 回、複合書式指定メソッドによって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="32c63-386">The [ICustomFormatter](xref:System.ICustomFormatter) interface has a single method, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), that is called automatically by a composite formatting method, once for each format item in a composite format string.</span></span> <span data-ttu-id="32c63-387">[Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドには、3 つのパラメーターがあります。書式指定項目の *formatString* 引数を表す書式指定文字列、書式を設定するオブジェクト、および書式指定サービスを提供する [IFormatProvider](xref:System.IFormatProvider) オブジェクトの 3 つです。</span><span class="sxs-lookup"><span data-stu-id="32c63-387">The [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method has three parameters: a format string, which represents the *formatString* argument in a format item, an object to format, and an [IFormatProvider](xref:System.IFormatProvider) object that provides formatting services.</span></span> <span data-ttu-id="32c63-388">通常は、[ICustomFormatter](xref:System.ICustomFormatter) を実装するクラスでは [IFormatProvider](xref:System.IFormatProvider) も実装するため、この最後のパラメーターはカスタム書式指定クラス自体への参照になります。</span><span class="sxs-lookup"><span data-stu-id="32c63-388">Typically, the class that implements [ICustomFormatter](xref:System.ICustomFormatter) also implements [IFormatProvider](xref:System.IFormatProvider), so this last parameter is a reference to the custom formatting class itself.</span></span> <span data-ttu-id="32c63-389">このメソッドは、書式を設定するオブジェクトのカスタム書式の文字列形式を返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-389">The method returns a custom formatted string representation of the object to be formatted.</span></span> <span data-ttu-id="32c63-390">オブジェクトの書式を設定できない場合は、null 参照を返します。</span><span class="sxs-lookup"><span data-stu-id="32c63-390">If the method cannot format the object, it should return a null reference.</span></span>

<span data-ttu-id="32c63-391">整数値を 2 桁の 16 進値とそれに続く 1 つの空白のシーケンスとして表示する、`ByteByByteFormatter` という名前の [ICustomFormatter](xref:System.ICustomFormatter) の実装の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-391">The following example provides an [ICustomFormatter](xref:System.ICustomFormatter) implementation named `ByteByByteFormatter` that displays integer values as a sequence of two-digit hexadecimal values followed by a space.</span></span>

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

<span data-ttu-id="32c63-392">`ByteByByteFormatter` クラスを使用して整数値の書式を設定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-392">The following example uses the `ByteByByteFormatter` class to format integer values.</span></span> <span data-ttu-id="32c63-393">[ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドが 2 回目の [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッド呼び出しで複数回呼び出されることに注意してください。また、`.ByteByByteFormatter.Format` メソッドが "N0" 書式指定文字列を認識せず、null 参照を返すため、3 回目のメソッド呼び出しでは既定の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロバイダーが使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32c63-393">Note that the [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method is called more than once in the second [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method call, and that the default [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) provider is used in the third method call because the `.ByteByByteFormatter.Format` method does not recognize the "N0" format string and returns a null reference.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a><span data-ttu-id="32c63-394">関連トピック</span><span class="sxs-lookup"><span data-stu-id="32c63-394">Related topics</span></span>

<span data-ttu-id="32c63-395">タイトル</span><span class="sxs-lookup"><span data-stu-id="32c63-395">Title</span></span> | <span data-ttu-id="32c63-396">定義</span><span class="sxs-lookup"><span data-stu-id="32c63-396">Definition</span></span>
----- | ----------
[<span data-ttu-id="32c63-397">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-397">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="32c63-398">数値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-398">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="32c63-399">カスタム数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-399">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="32c63-400">数値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-400">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="32c63-401">標準の日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-401">Standard date and time format strings</span></span>](standard-datetime.md) |  <span data-ttu-id="32c63-402">[DateTime](xref:System.DateTime) 値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-402">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="32c63-403">カスタム日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-403">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="32c63-404">[DateTime](xref:System.DateTime) 値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-404">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="32c63-405">標準 TimeSpan 書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-405">Standard TimeSpan format strings</span></span>](standard-timespan.md) | <span data-ttu-id="32c63-406">時間間隔に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-406">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="32c63-407">カスタム TimeSpan 書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-407">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="32c63-408">時間間隔に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-408">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="32c63-409">列挙型書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="32c63-409">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="32c63-410">列挙型の文字列形式を作成するために使用される標準書式指定文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-410">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
[<span data-ttu-id="32c63-411">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="32c63-411">Composite formatting</span></span>](composite-format.md) | <span data-ttu-id="32c63-412">文字列に 1 つ以上の書式指定された値を埋め込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-412">Describes how to embed one or more formatted values in a string.</span></span> <span data-ttu-id="32c63-413">この文字列は、コンソールに表示したり、ストリームに書き込んだりできます。</span><span class="sxs-lookup"><span data-stu-id="32c63-413">The string can subsequently be displayed on the console or written to a stream.</span></span>
[<span data-ttu-id="32c63-414">書式設定操作の実行</span><span class="sxs-lookup"><span data-stu-id="32c63-414">Performing formatting operations</span></span>](performing-formatting-operations.md) | <span data-ttu-id="32c63-415">特定の書式設定操作を行うための手順を説明するトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="32c63-415">Lists topics that provide step-by-step instructions for performing specific formatting operations.</span></span>
[<span data-ttu-id="32c63-416">文字列の解析</span><span class="sxs-lookup"><span data-stu-id="32c63-416">Parsing strings</span></span>](parsing-strings.md) | <span data-ttu-id="32c63-417">オブジェクトの文字列表現によって指定された値にオブジェクトを初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32c63-417">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="32c63-418">解析は書式設定の逆の操作です。</span><span class="sxs-lookup"><span data-stu-id="32c63-418">Parsing is the inverse operation of formatting.</span></span>

## <a name="reference"></a><span data-ttu-id="32c63-419">参照</span><span class="sxs-lookup"><span data-stu-id="32c63-419">Reference</span></span>

[<span data-ttu-id="32c63-420">System.IFormattable</span><span class="sxs-lookup"><span data-stu-id="32c63-420">System.IFormattable</span></span>](xref:System.IFormattable)

[<span data-ttu-id="32c63-421">System.IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="32c63-421">System.IFormatProvider</span></span>](xref:System.IFormatProvider)

[<span data-ttu-id="32c63-422">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="32c63-422">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

