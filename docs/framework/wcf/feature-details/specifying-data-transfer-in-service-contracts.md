---
title: サービス コントラクトでのデータ転送の指定
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 38
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc64ff14c321bd2053b0a97b3cf1ac075b02e973
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="34268-102">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="34268-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="34268-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、一種のメッセージング インフラストラクチャと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="34268-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="34268-104">サービス操作では、メッセージを受信し、それらのメッセージを処理し、送信することができます。</span><span class="sxs-lookup"><span data-stu-id="34268-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="34268-105">メッセージは、操作コントラクトを使用して記述されます。</span><span class="sxs-lookup"><span data-stu-id="34268-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="34268-106">たとえば、次のようなコントラクトがあるとします。</span><span class="sxs-lookup"><span data-stu-id="34268-106">For example, consider the following contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 <span data-ttu-id="34268-107">この場合、`GetAirfare` 操作では、`fromCity` と `toCity` に関する情報を含むメッセージを受け入れ、数値を含むメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="34268-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="34268-108">ここでは、操作コントラクトでメッセージを記述するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="34268-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="34268-109">パラメーターを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="34268-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="34268-110">メッセージを記述する最も簡単な方法は、パラメーター リストと戻り値を使用することです。</span><span class="sxs-lookup"><span data-stu-id="34268-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="34268-111">前の例では、`fromCity` と `toCity` の 2 つの文字列パラメーターを使用して要求メッセージを記述し、float 型の戻り値を使用して応答メッセージを記述しました。</span><span class="sxs-lookup"><span data-stu-id="34268-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="34268-112">戻り値だけでは応答メッセージを記述できない場合は、out パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34268-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="34268-113">たとえば、次の操作は、`fromCity` と `toCity` を要求メッセージに含め、数値と通貨を応答メッセージに含めます。</span><span class="sxs-lookup"><span data-stu-id="34268-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="34268-114">また、参照パラメーターを使用すると、要求メッセージと応答メッセージの両方のパラメーター部分を作成できます。</span><span class="sxs-lookup"><span data-stu-id="34268-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="34268-115">パラメーターは、シリアル化 (XML への変換) が可能な型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="34268-116">既定では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、<xref:System.Runtime.Serialization.DataContractSerializer> クラスというコンポーネントを使用してこの変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="34268-116">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="34268-117">ほとんどのプリミティブ型 (`int`、`string`、`float`、`DateTime` など) がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="34268-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="34268-118">ユーザー定義型には、通常、データ コントラクトが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="34268-119">詳細については、次を参照してください。[を使用してデータ コントラクト](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 <span data-ttu-id="34268-120">場合によっては、使用する型のシリアル化に `DataContractSerializer` が適さないことがあります。</span><span class="sxs-lookup"><span data-stu-id="34268-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="34268-121"> は、代替のシリアル化エンジンとして <xref:System.Xml.Serialization.XmlSerializer> をサポートしているため、パラメーターのシリアル化にこれを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="34268-121"> supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="34268-122"><xref:System.Xml.Serialization.XmlSerializer> では、`XmlAttributeAttribute` などの属性を使用することによって、結果の XML をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="34268-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="34268-123">特定の操作やサービス全体で <xref:System.Xml.Serialization.XmlSerializer> を使用するように切り替えるには、<xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を操作またはサービスに適用します。</span><span class="sxs-lookup"><span data-stu-id="34268-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="34268-124">例えば:</span><span class="sxs-lookup"><span data-stu-id="34268-124">For example:</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 <span data-ttu-id="34268-125">詳細については、次を参照してください。 [XmlSerializer クラスを使用して](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="34268-126">「XmlSerializer の使用」で説明するような明確な理由がある場合を除き、ここで示す <xref:System.Xml.Serialization.XmlSerializer> への手動での切り替えはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="34268-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="34268-127">.NET パラメーター名をコントラクト名から分離するには、<xref:System.ServiceModel.MessageParameterAttribute> 属性を使用し、`Name` プロパティを使用してコントラクト名を設定します。</span><span class="sxs-lookup"><span data-stu-id="34268-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="34268-128">たとえば、次の操作コントラクトは、このトピックの最初の例に相当します。</span><span class="sxs-lookup"><span data-stu-id="34268-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a><span data-ttu-id="34268-129">空のメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="34268-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="34268-130">空の要求メッセージを記述するには、入力パラメーターや参照パラメーターを一切指定しません。</span><span class="sxs-lookup"><span data-stu-id="34268-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="34268-131">C# の場合:</span><span class="sxs-lookup"><span data-stu-id="34268-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="34268-132">VB の場合:</span><span class="sxs-lookup"><span data-stu-id="34268-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="34268-133">空の応答メッセージを記述するには、戻り値の型として `void` を指定し、出力パラメーターや参照パラメーターを一切指定しません。</span><span class="sxs-lookup"><span data-stu-id="34268-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="34268-134">次の場合:</span><span class="sxs-lookup"><span data-stu-id="34268-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="34268-135">これは、次のような一方向操作コントラクトと異なります。</span><span class="sxs-lookup"><span data-stu-id="34268-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="34268-136">`SetTemperatureStatus` 操作は空のメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="34268-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="34268-137">入力メッセージの処理中にエラーが発生した場合は、代わりにエラーを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34268-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="34268-138">`SetLightbulbStatus` 操作は何も返しません。</span><span class="sxs-lookup"><span data-stu-id="34268-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="34268-139">この操作からエラー状態を伝達することはできません。</span><span class="sxs-lookup"><span data-stu-id="34268-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="34268-140">メッセージ コントラクトを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="34268-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="34268-141">1 つの型を使用してメッセージ全体を表現する場合があります。</span><span class="sxs-lookup"><span data-stu-id="34268-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="34268-142">この場合、データ コントラクトを使用することもできますが、メッセージ コントラクトを使用する方法をお勧めします。この方法を使用すると、結果の XML での不要なレベルのラップを回避できます。</span><span class="sxs-lookup"><span data-stu-id="34268-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="34268-143">さらに、メッセージ コントラクトを使用すると、結果のメッセージをより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="34268-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="34268-144">たとえば、メッセージの本文とヘッダーに含める情報をそれぞれ決めることができます。</span><span class="sxs-lookup"><span data-stu-id="34268-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="34268-145">次に、メッセージ コントラクトの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="34268-145">The following example shows the use of message contracts.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>   
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 <span data-ttu-id="34268-146">詳細については、次を参照してください。[メッセージ コントラクトを使用して](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="34268-147">前の例でも <xref:System.Runtime.Serialization.DataContractSerializer> クラスが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="34268-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="34268-148">メッセージ コントラクトで、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="34268-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="34268-149">これを行うには、操作またはコントラクトに <xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を適用し、メッセージ ヘッダーと本文メンバーで <xref:System.Xml.Serialization.XmlSerializer> クラスと互換性のある型を使用します。</span><span class="sxs-lookup"><span data-stu-id="34268-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="34268-150">ストリームを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="34268-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="34268-151">操作でメッセージを記述する場合は、<xref:System.IO.Stream> クラスまたはその派生クラスを操作コントラクトで使用したり、メッセージ コントラクト本文メンバー (この場合、唯一のメンバーである必要があります) として使用したりする方法もあります。</span><span class="sxs-lookup"><span data-stu-id="34268-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="34268-152">受信メッセージの場合、型は `Stream` である必要があり、派生クラスを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="34268-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="34268-153">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、シリアライザーを呼び出す代わりに、ストリームからデータを取得して送信メッセージに直接配置するか、受信メッセージからデータを取得してストリームに直接配置します。</span><span class="sxs-lookup"><span data-stu-id="34268-153">Instead of invoking the serializer, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="34268-154">次に、ストリームの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="34268-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="34268-155">1 つのメッセージ本文で `Stream` と非ストリーム データを組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="34268-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="34268-156">追加データをメッセージ ヘッダーに配置するには、メッセージ コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="34268-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="34268-157">操作コントラクトを定義するときのストリームの不適切な使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="34268-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 <span data-ttu-id="34268-158">操作コントラクトを定義するときのストリームの正しい使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="34268-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 <span data-ttu-id="34268-159">詳細については、次を参照してください。[大量のデータとストリーミング](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="34268-160">メッセージ クラスの使用</span><span class="sxs-lookup"><span data-stu-id="34268-160">Using the Message Class</span></span>  
 <span data-ttu-id="34268-161">送受信されるメッセージをプログラムによって完全に制御するには、次のコード例に示すように <xref:System.ServiceModel.Channels.Message> クラスを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="34268-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="34268-162">これで詳しく説明されている高度なシナリオは、[メッセージ クラスを使用して](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="34268-163">エラー メッセージの記述</span><span class="sxs-lookup"><span data-stu-id="34268-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="34268-164">一方向ではない操作では、戻り値と出力パラメーターまたは参照パラメーターによって記述されるメッセージに加え、通常の応答メッセージとエラー メッセージの少なくとも 2 つのメッセージを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="34268-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="34268-165">たとえば、次の操作コントラクトがあるとします。</span><span class="sxs-lookup"><span data-stu-id="34268-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="34268-166">この操作は、`float` 型の数値を含む通常のメッセージか、エラー コードと説明を含むエラー メッセージのいずれかを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="34268-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="34268-167">これは、サービス実装で <xref:System.ServiceModel.FaultException> をスローすることによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="34268-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="34268-168"><xref:System.ServiceModel.FaultContractAttribute> 属性を使用すると、追加のエラー メッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="34268-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="34268-169">追加のエラーは、次のコード例に示すように、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 <span data-ttu-id="34268-170">これらの追加エラーは、適切なデータ コントラクト型の <xref:System.ServiceModel.FaultException%601> をスローすることによって生成できます。</span><span class="sxs-lookup"><span data-stu-id="34268-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="34268-171">詳細については、次を参照してください。[例外の処理とエラー](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="34268-172"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用してエラーを記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="34268-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="34268-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> は、エラー コントラクトに影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="34268-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="34268-174">派生型の使用</span><span class="sxs-lookup"><span data-stu-id="34268-174">Using Derived Types</span></span>  
 <span data-ttu-id="34268-175">操作コントラクトやメッセージ コントラクトで基本型を使用し、その後、実際に操作を呼び出すときに派生型を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="34268-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="34268-176">この場合、<xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性または何らかの代替機構を使用して、派生型を使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="34268-177">次の操作があるとします。</span><span class="sxs-lookup"><span data-stu-id="34268-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="34268-178">`Book` から派生する `Magazine` と `LibraryItem` の 2 つの型があると想定します。</span><span class="sxs-lookup"><span data-stu-id="34268-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="34268-179">`IsLibraryItemAvailable` 操作でこれらの型を使用するには、操作を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="34268-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="34268-180">既定の <xref:System.Runtime.Serialization.KnownTypeAttribute> を使用している場合は、次のコード例に示すように <xref:System.Runtime.Serialization.DataContractSerializer> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="34268-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted   
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 <span data-ttu-id="34268-181"><xref:System.Xml.Serialization.XmlIncludeAttribute> を使用する場合は、<xref:System.Xml.Serialization.XmlSerializer> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="34268-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="34268-182"><xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性は、操作に適用することもサービス全体に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="34268-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="34268-183">この属性は、<xref:System.Runtime.Serialization.KnownTypeAttribute> 属性と同様に、型を受け取るか、既知の型の一覧を取得するために呼び出すメソッドの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="34268-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="34268-184">詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="34268-185">Use と Style の指定</span><span class="sxs-lookup"><span data-stu-id="34268-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="34268-186">Web サービス記述言語 (WSDL: Web Services Description Language) を使用してサービスを記述するときは、一般にドキュメントとリモート プロシージャ コール (RPC: Remote Procedure Call) の 2 つのスタイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="34268-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="34268-187">ドキュメント スタイルでは、スキーマを使用してメッセージ本文全体が記述されます。WSDL では、該当するスキーマの中の要素を参照して、メッセージ本文のさまざまな部分を記述します。</span><span class="sxs-lookup"><span data-stu-id="34268-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="34268-188">RPC スタイルでは、WSDL は、要素ではなく、メッセージの各部を表すスキーマ型を参照します。</span><span class="sxs-lookup"><span data-stu-id="34268-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="34268-189">場合によっては、これらのスタイルのいずれかを手動で選択することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="34268-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="34268-190">これを行うには、<xref:System.ServiceModel.DataContractFormatAttribute> 属性を適用し、`Style` プロパティを設定するか (<xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合)、`Style` 属性の <xref:System.ServiceModel.XmlSerializerFormatAttribute> を設定します (<xref:System.Xml.Serialization.XmlSerializer> を使用している場合)。</span><span class="sxs-lookup"><span data-stu-id="34268-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="34268-191">また、<xref:System.Xml.Serialization.XmlSerializer> はシリアル化された XML の形式を 2 とおり (`Literal` および `Encoded`) サポートしています。</span><span class="sxs-lookup"><span data-stu-id="34268-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="34268-192">`Literal` は最も一般に受け入れられたフォームであり、<xref:System.Runtime.Serialization.DataContractSerializer> がサポートする唯一のフォームです。</span><span class="sxs-lookup"><span data-stu-id="34268-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="34268-193">`Encoded` は SOAP 仕様のセクション 5 に記載されたレガシ フォームであり、新しいサービスにはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="34268-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="34268-194">`Encoded` モードに切り替えるには、`Use` 属性の <xref:System.ServiceModel.XmlSerializerFormatAttribute> プロパティを `Encoded` に設定します。</span><span class="sxs-lookup"><span data-stu-id="34268-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="34268-195">ほとんどの場合、`Style` プロパティと `Use` プロパティの既定の設定は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="34268-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="34268-196">シリアル化プロセスの制御</span><span class="sxs-lookup"><span data-stu-id="34268-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="34268-197">データをシリアル化する方法をカスタマイズする場合、さまざまな設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="34268-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="34268-198">サーバーのシリアル化設定の変更</span><span class="sxs-lookup"><span data-stu-id="34268-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="34268-199">既定の <xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合は、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をサービスに適用することで、サービスでのシリアル化プロセスの一部の側面を制御できます。</span><span class="sxs-lookup"><span data-stu-id="34268-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="34268-200">具体的には、`MaxItemsInObjectGraph` プロパティを使用して、<xref:System.Runtime.Serialization.DataContractSerializer> が逆シリアル化するオブジェクトの最大数を制限するクォータを設定できます。</span><span class="sxs-lookup"><span data-stu-id="34268-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="34268-201">また、`IgnoreExtensionDataObject` プロパティを使用すると、ラウンド トリップ バージョン管理機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="34268-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="34268-202"> クォータを参照してください[データのセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-202"> quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="34268-203"> ラウンド トリップを参照してください[上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-203"> round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a><span data-ttu-id="34268-204">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="34268-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="34268-205">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、特定の操作で使用しているシリアライザーに応じて自動的にプラグインされる、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> と <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> の 2 つの動作が用意されています。</span><span class="sxs-lookup"><span data-stu-id="34268-205">Two behaviors are available in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="34268-206">これらの動作は自動的に適用されるため、通常、これらの動作を意識する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34268-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="34268-207">ただし、`DataContractSerializerOperationBehavior` には、`MaxItemsInObjectGraph`、`IgnoreExtensionDataObject`、および `DataContractSurrogate` の 3 つのプロパティがあり、これらを使用してシリアル化プロセスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="34268-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="34268-208">最初の 2 つのプロパティの意味は、前のセクションの説明と同じです。</span><span class="sxs-lookup"><span data-stu-id="34268-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="34268-209">`DataContractSurrogate` プロパティを使用すると、シリアル化プロセスをカスタマイズおよび拡張するための強力な機構であるデータ コントラクト サロゲートを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="34268-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="34268-210">詳細については、次を参照してください。[データ コントラクト サロゲート](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="34268-211">`DataContractSerializerOperationBehavior` を使用すると、クライアントとサーバーの両方のシリアル化をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="34268-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="34268-212">クライアントで `MaxItemsInObjectGraph` クォータを増やす方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="34268-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
 <span data-ttu-id="34268-213">自己ホスト型サービスでの同等のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="34268-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 <span data-ttu-id="34268-214">Web ホスト型の場合は、新しい `ServiceHost` 派生クラスを作成し、サービス ホスト ファクトリを使用してプラグインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="34268-215">構成でのシリアル化設定の制御</span><span class="sxs-lookup"><span data-stu-id="34268-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="34268-216">次の例に示すように、`MaxItemsInObjectGraph` と `IgnoreExtensionDataObject` は、`dataContractSerializer` エンドポイントまたはサービスの動作を使用して構成によって制御できます。</span><span class="sxs-lookup"><span data-stu-id="34268-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="34268-217">共有する型のシリアル化、オブジェクト グラフの保存、およびカスタム シリアライザー</span><span class="sxs-lookup"><span data-stu-id="34268-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="34268-218"><xref:System.Runtime.Serialization.DataContractSerializer> は、.NET 型名ではなく、データ コントラクト名を使用してシリアル化を実行します。</span><span class="sxs-lookup"><span data-stu-id="34268-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="34268-219">これは、サービス指向アーキテクチャの基本思想と一致しており、高度な柔軟性の実現を可能にします。つまり、ネットワーク コントラクトに影響を及ぼさずに .NET 型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="34268-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="34268-220">まれなケースとして、実際の .NET 型名をシリアル化することにより、.NET Framework リモート処理テクノロジと同様のクライアントとサーバー間の密結合を導入することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="34268-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="34268-221">.NET Framework リモート処理から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行時に発生するまれなケースを除き、これはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="34268-221">This is not a recommended practice, except in rare cases that usually occur when migrating to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] from .NET Framework remoting.</span></span> <span data-ttu-id="34268-222">この場合、<xref:System.Runtime.Serialization.NetDataContractSerializer> クラスではなく、<xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="34268-223"><xref:System.Runtime.Serialization.DataContractSerializer> は、通常、オブジェクト グラフをオブジェクト ツリーとしてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="34268-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="34268-224">つまり、同じオブジェクトが複数回にわたって参照される場合、そのオブジェクトは複数回にわたってシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="34268-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="34268-225">たとえば、`PurchaseOrder` および `billTo` という、Address 型の 2 つのフィールドを持つ `shipTo` インスタンスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="34268-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="34268-226">この両方のフィールドに同じ Address インスタンスを設定すると、シリアル化および逆シリアル化の後に 2 つの同一の Address インスタンスが生じます。</span><span class="sxs-lookup"><span data-stu-id="34268-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="34268-227">これは、オブジェクト グラフを XML で表現する相互運用可能な標準の方法がないためです (ただし、<xref:System.Xml.Serialization.XmlSerializer> と `Style` に関する前のセクションで説明した `Use` で使用できる従来の SOAP エンコード標準を除きます)。</span><span class="sxs-lookup"><span data-stu-id="34268-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="34268-228">オブジェクト グラフをツリーとしてシリアル化する場合、循環参照が含まれたグラフをシリアル化できないなどの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="34268-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="34268-229">場合によっては、相互運用が可能ではありませんが、真のオブジェクト グラフ シリアル化に切り替えることが必要になります。</span><span class="sxs-lookup"><span data-stu-id="34268-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="34268-230">これを行うには、<xref:System.Runtime.Serialization.DataContractSerializer> パラメーターを `preserveObjectReferences` に設定して構築した `true` を使用します。</span><span class="sxs-lookup"><span data-stu-id="34268-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="34268-231">シナリオによっては、組み込みのシリアライザーでは不十分な場合があります。</span><span class="sxs-lookup"><span data-stu-id="34268-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="34268-232">ただし、ほとんどの場合、<xref:System.Runtime.Serialization.XmlObjectSerializer> と <xref:System.Runtime.Serialization.DataContractSerializer> の派生元である <xref:System.Runtime.Serialization.NetDataContractSerializer> 抽象クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34268-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="34268-233">前の 3 つのケース (.NET 型の保存、オブジェクト グラフの保存、および `XmlObjectSerializer` ベースの完全なカスタム シリアル化) では、必ずカスタム シリアライザーをプラグインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34268-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="34268-234">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="34268-234">To do this, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="34268-235"><xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> から派生する独自の動作を記述します。</span><span class="sxs-lookup"><span data-stu-id="34268-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2.  <span data-ttu-id="34268-236">独自のシリアライザー (`CreateSerializer`、<xref:System.Runtime.Serialization.NetDataContractSerializer> が <xref:System.Runtime.Serialization.DataContractSerializer> に設定された `preserveObjectReferences`、独自のカスタム `true` のいずれか) を返すように 2 つの <xref:System.Runtime.Serialization.XmlObjectSerializer> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="34268-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3.  <span data-ttu-id="34268-237">サービス ホストを開いたり、クライアント チャネルを作成したりする前に、既存の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 動作を削除し、前の手順で作成したカスタム派生クラスをプラグインします。</span><span class="sxs-lookup"><span data-stu-id="34268-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="34268-238"> シリアル化の概念の詳細を参照してください[シリアル化および逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)です。</span><span class="sxs-lookup"><span data-stu-id="34268-238"> advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34268-239">関連項目</span><span class="sxs-lookup"><span data-stu-id="34268-239">See Also</span></span>  
 [<span data-ttu-id="34268-240">XmlSerializer クラスの使用</span><span class="sxs-lookup"><span data-stu-id="34268-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [<span data-ttu-id="34268-241">方法 : ストリーミングを有効にする</span><span class="sxs-lookup"><span data-stu-id="34268-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [<span data-ttu-id="34268-242">方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="34268-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
