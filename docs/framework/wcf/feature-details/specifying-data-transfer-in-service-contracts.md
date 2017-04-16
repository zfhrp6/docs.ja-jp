---
title: "サービス コントラクトでのデータ転送の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス コントラクト [WCF], データ転送"
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 38
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 38
---
# サービス コントラクトでのデータ転送の指定
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、一種のメッセージング インフラストラクチャと考えることができます。サービス操作では、メッセージを受信し、それらのメッセージを処理し、送信することができます。メッセージは、操作コントラクトを使用して記述されます。たとえば、次のようなコントラクトがあるとします。  
  
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
  
 この場合、`GetAirfare` 操作では、`fromCity` と `toCity` に関する情報を含むメッセージを受け入れ、数値を含むメッセージを返します。  
  
 ここでは、操作コントラクトでメッセージを記述するさまざまな方法について説明します。  
  
## パラメーターを使用したメッセージの記述  
 メッセージを記述する最も簡単な方法は、パラメーター リストと戻り値を使用することです。前の例では、`fromCity` と `toCity` の 2 つの文字列パラメーターを使用して要求メッセージを記述し、float 型の戻り値を使用して応答メッセージを記述しました。戻り値だけでは応答メッセージを記述できない場合は、out パラメーターを使用できます。たとえば、次の操作は、`fromCity` と `toCity` を要求メッセージに含め、数値と通貨を応答メッセージに含めます。  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 また、参照パラメーターを使用すると、要求メッセージと応答メッセージの両方のパラメーター部分を作成できます。パラメーターは、シリアル化 \(XML への変換\) が可能な型にする必要があります。既定では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、<xref:System.Runtime.Serialization.DataContractSerializer> クラスというコンポーネントを使用してこの変換を実行します。ほとんどのプリミティブ型 \(`int`、`string`、`float`、`DateTime` など\) がサポートされます。ユーザー定義型には、通常、データ コントラクトが存在する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```  
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
  
 場合によっては、使用する型のシリアル化に `DataContractSerializer` が適さないことがあります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、代替のシリアル化エンジンとして <xref:System.Xml.Serialization.XmlSerializer> をサポートしているため、パラメーターのシリアル化にこれを使用することもできます。<xref:System.Xml.Serialization.XmlSerializer> では、`XmlAttributeAttribute` などの属性を使用することによって、結果の XML をより細かく制御できます。特定の操作やサービス全体で <xref:System.Xml.Serialization.XmlSerializer> を使用するように切り替えるには、<xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を操作またはサービスに適用します。次に例を示します。  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [XmlSerializer クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).「XmlSerializer の使用」で説明するような明確な理由がある場合を除き、ここで示す <xref:System.Xml.Serialization.XmlSerializer> への手動での切り替えはお勧めしません。  
  
 .NET パラメーター名をコントラクト名から分離するには、<xref:System.ServiceModel.MessageParameterAttribute> 属性を使用し、`Name` プロパティを使用してコントラクト名を設定します。たとえば、次の操作コントラクトは、このトピックの最初の例に相当します。  
  
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
  
## 空のメッセージの記述  
 空の要求メッセージを記述するには、入力パラメーターや参照パラメーターを一切指定しません。C\# の場合:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 VB の場合:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 空の応答メッセージを記述するには、戻り値の型として `void` を指定し、出力パラメーターや参照パラメーターを一切指定しません。たとえば:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
  
```  
  
 これは、次のような一方向操作コントラクトと異なります。  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
  
```  
  
 `SetTemperatureStatus` 操作は空のメッセージを返します。入力メッセージの処理中にエラーが発生した場合は、代わりにエラーを返す可能性があります。`SetLightbulbStatus` 操作は何も返しません。この操作からエラー状態を伝達することはできません。  
  
## メッセージ コントラクトを使用したメッセージの記述  
 1 つの型を使用してメッセージ全体を表現する場合があります。この場合、データ コントラクトを使用することもできますが、メッセージ コントラクトを使用する方法をお勧めします。この方法を使用すると、結果の XML での不要なレベルのラップを回避できます。さらに、メッセージ コントラクトを使用すると、結果のメッセージをより細かく制御できます。たとえば、メッセージの本文とヘッダーに含める情報をそれぞれ決めることができます。次に、メッセージ コントラクトの使用例を示します。  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [メッセージ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 前の例でも <xref:System.Runtime.Serialization.DataContractSerializer> クラスが既定で使用されます。メッセージ コントラクトで、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用することもできます。これを行うには、操作またはコントラクトに <xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を適用し、メッセージ ヘッダーと本文メンバーで <xref:System.Xml.Serialization.XmlSerializer> クラスと互換性のある型を使用します。  
  
## ストリームを使用したメッセージの記述  
 操作でメッセージを記述する場合は、<xref:System.IO.Stream> クラスまたはその派生クラスを操作コントラクトで使用したり、メッセージ コントラクト本文メンバー \(この場合、唯一のメンバーである必要があります\) として使用したりする方法もあります。受信メッセージの場合、型は `Stream` である必要があり、派生クラスを使用することはできません。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、シリアライザーを呼び出す代わりに、ストリームからデータを取得して送信メッセージに直接配置するか、受信メッセージからデータを取得してストリームに直接配置します。次に、ストリームの使用例を示します。  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
  
```  
  
 1 つのメッセージ本文で `Stream` と非ストリーム データを組み合わせることはできません。追加データをメッセージ ヘッダーに配置するには、メッセージ コントラクトを使用します。操作コントラクトを定義するときのストリームの不適切な使用例を次に示します。  
  
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
  
 操作コントラクトを定義するときのストリームの正しい使用例を次に示します。  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [大規模データとストリーミング](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## メッセージ クラスの使用  
 送受信されるメッセージをプログラムによって完全に制御するには、次のコード例に示すように <xref:System.ServiceModel.Channels.Message> クラスを直接使用します。  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
  
```  
  
 これは高度なシナリオです。詳細については、「[メッセージ クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)」を参照してください。  
  
## エラー メッセージの記述  
 一方向ではない操作では、戻り値と出力パラメーターまたは参照パラメーターによって記述されるメッセージに加え、通常の応答メッセージとエラー メッセージの少なくとも 2 つのメッセージを返すことができます。たとえば、次の操作コントラクトがあるとします。  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
  
```  
  
 この操作は、`float` 型の数値を含む通常のメッセージか、エラー コードと説明を含むエラー メッセージのいずれかを返すことができます。これは、サービス実装で <xref:System.ServiceModel.FaultException> をスローすることによって実現できます。  
  
 <xref:System.ServiceModel.FaultContractAttribute> 属性を使用すると、追加のエラー メッセージを指定できます。追加のエラーは、次のコード例に示すように、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化できる必要があります。  
  
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
  
 これらの追加エラーは、適切なデータ コントラクト型の <xref:System.ServiceModel.FaultException%601> をスローすることによって生成できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][例外とエラーの処理](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 <xref:System.Xml.Serialization.XmlSerializer> クラスを使用してエラーを記述することはできません。<xref:System.ServiceModel.XmlSerializerFormatAttribute> は、エラー コントラクトに影響を及ぼしません。  
  
## 派生型の使用  
 操作コントラクトやメッセージ コントラクトで基本型を使用し、その後、実際に操作を呼び出すときに派生型を使用する場合があります。この場合、<xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性または何らかの代替機構を使用して、派生型を使用できるようにする必要があります。次の操作があるとします。  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
```  
  
```vbs  
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
```  
  
 `LibraryItem` から派生する `Book` と `Magazine` の 2 つの型があると想定します。`IsLibraryItemAvailable` 操作でこれらの型を使用するには、操作を次のように変更します。  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 既定の <xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合は、次のコード例に示すように <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性を使用できます。  
  
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
  
 <xref:System.Xml.Serialization.XmlSerializer> を使用する場合は、<xref:System.Xml.Serialization.XmlIncludeAttribute> 属性を使用できます。  
  
 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性は、操作に適用することもサービス全体に適用することもできます。この属性は、<xref:System.Runtime.Serialization.KnownTypeAttribute> 属性と同様に、型を受け取るか、既知の型の一覧を取得するために呼び出すメソッドの名前を受け取ります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][既知のデータ コントラクト型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## Use と Style の指定  
 Web サービス記述言語 \(WSDL: Web Services Description Language\) を使用してサービスを記述するときは、一般にドキュメントとリモート プロシージャ コール \(RPC: Remote Procedure Call\) の 2 つのスタイルが使用されます。ドキュメント スタイルでは、スキーマを使用してメッセージ本文全体が記述されます。WSDL では、該当するスキーマの中の要素を参照して、メッセージ本文のさまざまな部分を記述します。RPC スタイルでは、WSDL は、要素ではなく、メッセージの各部を表すスキーマ型を参照します。場合によっては、これらのスタイルのいずれかを手動で選択することが必要になります。これを行うには、<xref:System.ServiceModel.DataContractFormatAttribute> 属性を適用し、`Style` プロパティを設定するか \(<xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合\)、<xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性の `Style` を設定します \(<xref:System.Xml.Serialization.XmlSerializer> を使用している場合\)。  
  
 また、<xref:System.Xml.Serialization.XmlSerializer> はシリアル化された XML の形式を 2 とおり \(`Literal` および `Encoded`\) サポートしています。`Literal` は最も一般に受け入れられたフォームであり、<xref:System.Runtime.Serialization.DataContractSerializer> がサポートする唯一のフォームです。`Encoded` は SOAP 仕様のセクション 5 に記載されたレガシ フォームであり、新しいサービスにはお勧めしません。`Encoded` モードに切り替えるには、<xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性の `Use` プロパティを `Encoded` に設定します。  
  
 ほとんどの場合、`Style` プロパティと `Use` プロパティの既定の設定は変更しないでください。  
  
## シリアル化プロセスの制御  
 データをシリアル化する方法をカスタマイズする場合、さまざまな設定を行うことができます。  
  
### サーバーのシリアル化設定の変更  
 既定の <xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合は、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をサービスに適用することで、サービスでのシリアル化プロセスの一部の側面を制御できます。具体的には、`MaxItemsInObjectGraph` プロパティを使用して、<xref:System.Runtime.Serialization.DataContractSerializer> が逆シリアル化するオブジェクトの最大数を制限するクォータを設定できます。また、`IgnoreExtensionDataObject` プロパティを使用すると、ラウンド トリップ バージョン管理機能を無効にできます。クォータ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[セキュリティに関するデータの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)」を参照してください。ラウンドトリップ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)」を参照してください。  
  
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
  
### シリアル化の動作  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、特定の操作で使用しているシリアライザーに応じて自動的にプラグインされる、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> と <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> の 2 つの動作が用意されています。これらの動作は自動的に適用されるため、通常、これらの動作を意識する必要はありません。  
  
 ただし、`DataContractSerializerOperationBehavior` には、`MaxItemsInObjectGraph`、`IgnoreExtensionDataObject`、および `DataContractSurrogate` の 3 つのプロパティがあり、これらを使用してシリアル化プロセスをカスタマイズできます。最初の 2 つのプロパティの意味は、前のセクションの説明と同じです。`DataContractSurrogate` プロパティを使用すると、シリアル化プロセスをカスタマイズおよび拡張するための強力な機構であるデータ コントラクト サロゲートを有効にできます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト サロゲート](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 `DataContractSerializerOperationBehavior` を使用すると、クライアントとサーバーの両方のシリアル化をカスタマイズできます。クライアントで `MaxItemsInObjectGraph` クォータを増やす方法を次の例に示します。  
  
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
  
 自己ホスト型サービスでの同等のコードを次に示します。  
  
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
  
 Web ホスト型の場合は、新しい `ServiceHost` 派生クラスを作成し、サービス ホスト ファクトリを使用してプラグインする必要があります。  
  
### 構成でのシリアル化設定の制御  
 次の例に示すように、`MaxItemsInObjectGraph` と `IgnoreExtensionDataObject` は、`dataContractSerializer` エンドポイントまたはサービスの動作を使用して構成によって制御できます。  
  
```  
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
  
### 共有する型のシリアル化、オブジェクト グラフの保存、およびカスタム シリアライザー  
 <xref:System.Runtime.Serialization.DataContractSerializer> は、.NET 型名ではなく、データ コントラクト名を使用してシリアル化を実行します。これは、サービス指向アーキテクチャの基本思想と一致しており、高度な柔軟性の実現を可能にします。つまり、ネットワーク コントラクトに影響を及ぼさずに .NET 型を変更できます。まれなケースとして、実際の .NET 型名をシリアル化することにより、.NET Framework リモート処理テクノロジと同様のクライアントとサーバー間の密結合を導入することが必要になる場合があります。.NET Framework リモート処理から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行時に発生するまれなケースを除き、これはお勧めしません。この場合、<xref:System.Runtime.Serialization.DataContractSerializer> クラスではなく、<xref:System.Runtime.Serialization.NetDataContractSerializer> クラスを使用する必要があります。  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> は、通常、オブジェクト グラフをオブジェクト ツリーとしてシリアル化します。つまり、同じオブジェクトが複数回にわたって参照される場合、そのオブジェクトは複数回にわたってシリアル化されます。たとえば、`billTo` および `shipTo` という、Address 型の 2 つのフィールドを持つ `PurchaseOrder` インスタンスがあるとします。この両方のフィールドに同じ Address インスタンスを設定すると、シリアル化および逆シリアル化の後に 2 つの同一の Address インスタンスが生じます。これは、オブジェクト グラフを XML で表現する相互運用可能な標準の方法がないためです \(ただし、`Style` と `Use` に関する前のセクションで説明した <xref:System.Xml.Serialization.XmlSerializer> で使用できる従来の SOAP エンコード標準を除きます\)。オブジェクト グラフをツリーとしてシリアル化する場合、循環参照が含まれたグラフをシリアル化できないなどの欠点があります。場合によっては、相互運用が可能ではありませんが、真のオブジェクト グラフ シリアル化に切り替えることが必要になります。これを行うには、`preserveObjectReferences` パラメーターを `true` に設定して構築した <xref:System.Runtime.Serialization.DataContractSerializer> を使用します。  
  
 シナリオによっては、組み込みのシリアライザーでは不十分な場合があります。ただし、ほとんどの場合、<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.NetDataContractSerializer> の派生元である <xref:System.Runtime.Serialization.XmlObjectSerializer> 抽象クラスを使用できます。  
  
 前述の 3 つのケース \(.NET 型の保存、オブジェクト グラフの保存、および `XmlObjectSerializer` ベースの完全なカスタム シリアル化\) では、必ずカスタム シリアライザーをプラグインする必要があります。これを行うには、次の手順を実行します:  
  
1.  <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> から派生する独自の動作を記述します。  
  
2.  独自のシリアライザー \(<xref:System.Runtime.Serialization.NetDataContractSerializer>、`preserveObjectReferences` が `true` に設定された <xref:System.Runtime.Serialization.DataContractSerializer>、独自のカスタム <xref:System.Runtime.Serialization.XmlObjectSerializer> のいずれか\) を返すように 2 つの `CreateSerializer` メソッドをオーバーライドします。  
  
3.  サービス ホストを開いたり、クライアント チャネルを作成したりする前に、既存の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 動作を削除し、前の手順で作成したカスタム派生クラスをプラグインします。  
  
 シリアル化の高度な概念[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[シリアル化と逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)」を参照してください。  
  
## 参照  
 [XmlSerializer クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)   
 [方法 : ストリーミングを有効にする](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)   
 [方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)