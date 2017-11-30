---
title: "文字列の .NET Framework データ型への変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="3e504-102">文字列の .NET Framework データ型への変換</span><span class="sxs-lookup"><span data-stu-id="3e504-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="3e504-103">文字列を .NET Framework データ型に変換する場合は、使用、 **XmlConvert**アプリケーション要件に適合するメソッド。</span><span class="sxs-lookup"><span data-stu-id="3e504-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="3e504-104">使用できるすべての変換方法の一覧については、 **XmlConvert**クラスを参照してください<xref:System.Xml.XmlConvert>です。</span><span class="sxs-lookup"><span data-stu-id="3e504-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="3e504-105">返される文字列、 **ToString**メソッドは渡されたデータの文字列バージョンです。</span><span class="sxs-lookup"><span data-stu-id="3e504-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="3e504-106">さらに、変換を使用していくつかの .NET Framework の型は、 **XmlConvert**クラス内のメソッドを使用していない、 **System.Convert**クラスです。</span><span class="sxs-lookup"><span data-stu-id="3e504-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="3e504-107">**XmlConvert**クラスは、XML スキーマ (XSD) データ型仕様に準拠しており、データ型を**XmlConvert**にマップできます。</span><span class="sxs-lookup"><span data-stu-id="3e504-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="3e504-108">次の表は、.NET Framework データ型の一覧と、XML スキーマ (XSD) のデータ型マップを使用した場合に返される文字列を示しています。</span><span class="sxs-lookup"><span data-stu-id="3e504-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="3e504-109">これらの .NET Framework 型を使用して処理することはできません**System.Convert**です。</span><span class="sxs-lookup"><span data-stu-id="3e504-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="3e504-110">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="3e504-110">.NET Framework type</span></span>|<span data-ttu-id="3e504-111">返される文字列</span><span class="sxs-lookup"><span data-stu-id="3e504-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="3e504-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="3e504-112">Boolean</span></span>|<span data-ttu-id="3e504-113">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="3e504-113">"true", "false"</span></span>|  
|<span data-ttu-id="3e504-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="3e504-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-115">"INF"</span></span>|  
|<span data-ttu-id="3e504-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="3e504-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-117">"-INF"</span></span>|  
|<span data-ttu-id="3e504-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="3e504-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-119">"INF"</span></span>|  
|<span data-ttu-id="3e504-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="3e504-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-121">"-INF"</span></span>|  
|<span data-ttu-id="3e504-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="3e504-122">DateTime</span></span>|<span data-ttu-id="3e504-123">形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="3e504-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="3e504-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="3e504-124">Timespan</span></span>|<span data-ttu-id="3e504-125">PnYnMnTnHnMnS の形式。つまり、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。</span><span class="sxs-lookup"><span data-stu-id="3e504-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3e504-126">文字列を使用して、表に示すいずれかの .NET Framework 型に変換する場合、 **ToString**メソッドで返される文字列は、基本型ですが、XML スキーマ (XSD) 文字列型ではありません。</span><span class="sxs-lookup"><span data-stu-id="3e504-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="3e504-127">**DateTime**と**Timespan**こととは異なる値型、 **DateTime**一方で、瞬間を表します、 **TimeSpan**時間間隔を表します。</span><span class="sxs-lookup"><span data-stu-id="3e504-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="3e504-128">**DateTime**と**Timespan**形式は、XML スキーマ (XSD) データ型仕様で指定されます。</span><span class="sxs-lookup"><span data-stu-id="3e504-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="3e504-129">例:</span><span class="sxs-lookup"><span data-stu-id="3e504-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="3e504-130">**出力**</span><span class="sxs-lookup"><span data-stu-id="3e504-130">**Output**</span></span>  
  
 <span data-ttu-id="3e504-131">`<Date>2001-08-04T00:00:00</Date>`。</span><span class="sxs-lookup"><span data-stu-id="3e504-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="3e504-132">整数を文字列に変換するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e504-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="3e504-133">**出力**</span><span class="sxs-lookup"><span data-stu-id="3e504-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="3e504-134">ただし、変更する場合は、文字列を**ブール**、**単一**、または**二重**、返される .NET Framework の型を使用する場合に返される型と同じではありません、**System.Convert**クラスです。</span><span class="sxs-lookup"><span data-stu-id="3e504-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="3e504-135">String から Boolean</span><span class="sxs-lookup"><span data-stu-id="3e504-135">String to Boolean</span></span>  
 <span data-ttu-id="3e504-136">次の表は、どのような生成される型、入力文字列を文字列に変換するときに**ブール**を使用して、 **ToBoolean**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3e504-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="3e504-137">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e504-137">Valid string input parameter</span></span>|<span data-ttu-id="3e504-138">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="3e504-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="3e504-139">"true"</span><span class="sxs-lookup"><span data-stu-id="3e504-139">"true"</span></span>|<span data-ttu-id="3e504-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="3e504-140">Boolean.True</span></span>|  
|<span data-ttu-id="3e504-141">"1"</span><span class="sxs-lookup"><span data-stu-id="3e504-141">"1"</span></span>|<span data-ttu-id="3e504-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="3e504-142">Boolean.True</span></span>|  
|<span data-ttu-id="3e504-143">"false"</span><span class="sxs-lookup"><span data-stu-id="3e504-143">"false"</span></span>|<span data-ttu-id="3e504-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="3e504-144">Boolean.False</span></span>|  
|<span data-ttu-id="3e504-145">"0"</span><span class="sxs-lookup"><span data-stu-id="3e504-145">"0"</span></span>|<span data-ttu-id="3e504-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="3e504-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="3e504-147">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="3e504-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="3e504-148">**入力**</span><span class="sxs-lookup"><span data-stu-id="3e504-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="3e504-149">次のコードによって認識できる両方と**bvalue**は**System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="3e504-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="3e504-150">String から Single</span><span class="sxs-lookup"><span data-stu-id="3e504-150">String to Single</span></span>  
 <span data-ttu-id="3e504-151">次の表は、どのような生成される型、入力文字列を文字列に変換するときに、**単一**を使用して、 **ToSingle**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3e504-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="3e504-152">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e504-152">Valid string input parameter</span></span>|<span data-ttu-id="3e504-153">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="3e504-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="3e504-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-154">"INF"</span></span>|<span data-ttu-id="3e504-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="3e504-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-156">"-INF"</span></span>|<span data-ttu-id="3e504-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="3e504-158">String から Double</span><span class="sxs-lookup"><span data-stu-id="3e504-158">String to Double</span></span>  
 <span data-ttu-id="3e504-159">次の表は、どのような生成される型、入力文字列を文字列に変換するときに、**単一**を使用して、 **ToDouble**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3e504-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="3e504-160">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e504-160">Valid string input parameter</span></span>|<span data-ttu-id="3e504-161">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="3e504-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="3e504-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-162">"INF"</span></span>|<span data-ttu-id="3e504-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="3e504-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="3e504-164">"-INF"</span></span>|<span data-ttu-id="3e504-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="3e504-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="3e504-166">次のコードは、`<Infinity>INF</Infinity>` を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3e504-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e504-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e504-167">See Also</span></span>  
 [<span data-ttu-id="3e504-168">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="3e504-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="3e504-169">.NET Framework の型を文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="3e504-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
