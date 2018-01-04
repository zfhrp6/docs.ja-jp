---
title: "カスタム メッセージ エンコーダー : カスタム テキスト エンコーダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54e2b87a9e104ea61c32b06ffc604fc864283f3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a>カスタム メッセージ エンコーダー : カスタム テキスト エンコーダー
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用してカスタム テキスト メッセージ エンコーダーを実装する方法を示します。  
  
> [!WARNING]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされているエンコーディングは、UTF-8、UTF-16、および Big Endean Unicode のみです。 このサンプルのカスタム テキスト メッセージ エンコーダーでは、すべてのプラットフォームでサポートされ、相互運用に必要とされる可能性のある文字エンコーディングがサポートされます。 このサンプルは、クライアント コンソール プログラム (.exe)、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll)、およびテキスト メッセージ エンコーダー ライブラリ (.dll) で構成されています。 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。 このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。 クライアントは指定された算術演算を同期要求し、サービスは結果と共に応答します。 クライアントとサービスはどちらも、既定の `CustomTextMessageEncoder` の代わりに <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> を使用します。  
  
 カスタム エンコーダーの実装は、メッセージ エンコーダー ファクトリ、メッセージ エンコーダー、メッセージ エンコーディング バインド要素、および構成ハンドラーで構成され、次が示されます。  
  
-   カスタム エンコーダーおよびエンコーダー ファクトリの作成。  
  
-   カスタム エンコーダーのバインディング要素の作成。  
  
-   カスタム バインド要素を統合するためのカスタム バインド構成の使用。  
  
-   カスタム バインド要素のファイル構成を可能にするカスタム構成ハンドラーの開発。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
3.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>メッセージ エンコーダー ファクトリとメッセージ エンコーダー  
 <xref:System.ServiceModel.ServiceHost> またはクライアント チャネルが開かれると、デザイン時コンポーネント `CustomTextMessageBindingElement` は `CustomTextMessageEncoderFactory` を作成します。 このファクトリは、`CustomTextMessageEncoder` を作成します。 メッセージ エンコーダーは、ストリーミング モードとバッファー モードの両方で動作し、 <xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を使用してメッセージの読み取りと書き込みを行います。 UTF-8、UTF-16、および Big-Endean Unicode だけをサポートするように最適化された [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の XML リーダーとライターとは異なり、これらのリーダーとライターはプラットフォームでサポートされるすべてのエンコーディングをサポートします。  
  
 カスタム テキスト メッセージ エンコーダーのコード例を次に示します。  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 メッセージ エンコーダー ファクトリを作成する方法を次のコード例に示します。  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a>メッセージ エンコーディング バインド要素  
 このバインディング要素により、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイム スタックの構成が可能になります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーション内でカスタム メッセージ エンコーダーを使用するには、ランタイム スタックの適切なレベルで適切な設定を使用してメッセージ エンコーダー ファクトリを作成する、バインディング要素が必要です。  
  
 `CustomTextMessageBindingElement` は <xref:System.ServiceModel.Channels.BindingElement> 基本クラスから派生し、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> クラスを継承します。 これによって、他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントは、このバインディング要素をメッセージ エンコーディング バインディング要素として認識できます。 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> を実装すると、一致するメッセージ エンコーダー ファクトリのインスタンスが適切に設定されて返されます。  
  
 `CustomTextMessageBindingElement` は、プロパティを介して `MessageVersion`、`ContentType`、および `Encoding` の設定を公開します。 エンコーダーは、Soap11Addressing と Soap12Addressing1 の両方のバージョンをサポートします。 既定値は Soap11Addressing1 です。 また、`ContentType` の既定値は "text/xml" です。 `Encoding` プロパティでは、必要な文字エンコーディングの値を設定できます。 サンプルのクライアントとサービスでは、ISO-8859-1 (Latin1) 文字エンコーディングを使用します。この規格は、<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではサポートされません。  
  
 カスタム テキスト メッセージ エンコーダーを使用してプログラムでバインディングを作成する方法を次のコードに示します。  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>メッセージ エンコーディング バインド要素へのメタデータのサポートの追加  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> から派生するすべての型は、サービスに対して生成される WSDL ドキュメント内の SOAP バインドのバージョンを更新します。 これを行うには、`ExportEndpoint` インターフェイス上に <xref:System.ServiceModel.Description.IWsdlExportExtension> メソッドを実装し、生成された WSDL を変更します。 このサンプルでは、`CustomTextMessageBindingElement` は `TextMessageEncodingBinidngElement` からの WSDL エクスポート ロジックを使用します。  
  
 このサンプルの場合、クライアント構成は手動構成です。 Svcutil.exe を使用してクライアント構成を生成することはできません。`CustomTextMessageBindingElement` では、動作を記述するポリシー アサーションがエクスポートされないからです。 通常は、カスタム バインディング要素上に <xref:System.ServiceModel.Description.IPolicyExportExtension> インターフェイスを実装して、バインディング要素によって実装される動作または機能を記述するカスタム ポリシー アサーションをエクスポートする必要があります。 カスタム バインド要素のポリシー アサーションをエクスポートする方法の例は、次を参照してください。、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。  
  
## <a name="message-encoding-binding-configuration-handler"></a>メッセージ エンコーディング バインド構成ハンドラー  
 前のセクションでは、カスタム テキスト メッセージ エンコーダーをプログラムによって使用する方法を示しました。 `CustomTextMessageEncodingBindingSection` は構成ハンドラーを実装します。この構成ハンドラーにより、カスタム テキスト メッセージ エンコーダーを構成ファイル内で使用することを指定できます。 `CustomTextMessageEncodingBindingSection` クラスは <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> クラスから派生します。 `BindingElementType` プロパティでは、このセクション用に作成するバインディング要素の型が構成システムに通知されます。  
  
 `CustomTextMessageBindingElement` によって定義されたすべての設定は、`CustomTextMessageEncodingBindingSection` のプロパティとして公開されます。 <xref:System.Configuration.ConfigurationPropertyAttribute> は、構成要素の属性をプロパティにマップしたり、属性がない場合は既定値を設定する際に役立ちます。 構成から値が読み込まれて型のプロパティに適用されると、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> メソッドが呼び出されます。このメソッドは、プロパティをバインディング要素の具体的なインスタンスに変換します。  
  
 この構成ハンドラーは、サービスまたはクライアントの App.config または Web.config の次の表現にマップされます。  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 このサンプルでは、ISO-8859-1 エンコーディングを使用します。  
  
 この構成ハンドラーを使用するには、次の構成要素を使用して登録する必要があります。  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a>参照
