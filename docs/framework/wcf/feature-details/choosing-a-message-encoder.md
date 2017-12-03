---
title: "メッセージ エンコーダーを選択する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 743e8cdf1a10efb7b99d6c6dcfcff611df6fbf4e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="choosing-a-message-encoder"></a>メッセージ エンコーダーを選択する
このトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に用意されているメッセージ エンコーダー (バイナリ、テキスト、および MTOM (Message Transmission Optimization Mechanism)) を選択する際の基準について説明します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、エンドポイント間で、ネットワーク経由でデータを転送する方法を指定する、*バインディング*、これで構成された一連の*バインド要素*です。 メッセージ エンコーダーは、バインディング スタックにあるメッセージ エンコーディング バインド要素によって表されます。 バインディングには、オプションのプロトコル バインド要素 (セキュリティ バインド要素や信頼できるメッセージング バインド要素など)、必須のメッセージ エンコーディング バインド要素、および必須のトランスポート バインド要素が含まれます。  
  
 メッセージ エンコーディング バインド要素は、オプションのプロトコル バインド要素の下、必須のトランスポート バインド要素の上に位置します。 送信側では、メッセージ エンコーダーにより出力 <xref:System.ServiceModel.Channels.Message> がシリアル化されてトランスポートに渡されます。 受信側では、メッセージ エンコーダーがトランスポートからシリアル化形式の <xref:System.ServiceModel.Channels.Message> を受信し、上位のプロトコル層が存在する場合はその層に、存在しない場合はアプリケーションに渡します。  
  
 既存のクライアントまたはサーバーに接続するときには、相手側が予測している方法でメッセージをエンコードする必要があるため、特定のメッセージ エンコーディングを選択できない場合があります。 ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成している場合は、サービスを複数のエンドポイントで公開し、それぞれで異なるメッセージ エンコーディングを使用できます。 これにより、クライアントは最適なエンドポイントでのサービスとの対話に最も適したエンコーディングを選択でき、最適なエンコーディングを選択する際の柔軟性が得られます。 複数のエンドポイントを使用することにより、異なるメッセージ エンコーディングの利点を他のバインド要素と組み合わせることも可能になります。  
  
## <a name="system-provided-encoders"></a>システム指定のエンコーダー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意された 3 種類のメッセージ エンコーダーは、次の 3 つのクラスによって表されます。  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> は、書式なし XML エンコーディングと SOAP エンコーディングの両方をサポートするテキスト メッセージ エンコーダーです。 テキスト メッセージ エンコーダーの書式なし XML エンコーディング モードは、テキスト ベースの SOAP エンコーディングと区別するために、"POX" (Plain Old XML) と呼ばれます。 POX を有効にするには、<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> プロパティを <xref:System.ServiceModel.Channels.MessageVersion.None%2A> に設定します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイント以外のエンドポイントと相互運用する場合は、テキスト メッセージ エンコーダーを使用します。  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> は、バイナリ メッセージ エンコーダーです。コンパクトなバイナリ形式を使用し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] との間の通信用に最適化されているため、相互運用できません。 このエンコーダーは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意された 3 種類のエンコーダーの中で、パフォーマンスが最も優れたエンコーダーでもあります。  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement -->`System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>、文字エンコーディング バインド要素を指定し、MTOM エンコーディングを使用してメッセージをメッセージのバージョン管理します。 MTOM は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージでのバイナリ データの転送に有効なテクノロジです。 MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。 MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックはテキストに変換せずにそのまま転送することによって最適化します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されたエンコーダーの中で、MTOM は効率面でテキスト エンコーダー (最も遅い) とバイナリ エンコーダー (最も速い) の中間に位置します。  
  
## <a name="how-to-choose-a-message-encoder"></a>メッセージ エンコーダーを選択する方法  
 メッセージ エンコーダーを選択するために使用される一般的な要因を、次の表に示します。 アプリケーションにとって重要な要因に優先順位を与えて、それらの要因に対して最適なメッセージ エンコーダーを選択します。 この表には示されていないその他の要因と、アプリケーションで必要になることがあるカスタム メッセージ エンコーダーも考慮するようにしてください。  
  
|要因|説明|この要因をサポートするエンコーダー|  
|------------|-----------------|---------------------------------------|  
|サポートされている文字セット|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>および <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> UTF8 と UTF16 Unicode のみのサポート (*ビッグ エンディアン*と*リトル エンディアン*) エンコーディング。 UTF7 や ASCII など、別のエンコーディングが要求される場合はカスタム エンコーディングを使用する必要があります。 サンプルのカスタム エンコーダーでは、次を参照してください。[カスタム メッセージ エンコーダー](http://go.microsoft.com/fwlink/?LinkId=119857)です。|テキスト|  
|検査|検査は、転送中にメッセージを調べる機能です。 SOAP の使用に関係なく、テキスト エンコーディングでは、多くのアプリケーションで特別なツールを使用することなくメッセージの検査と分析が可能です。 メッセージまたはトランスポートのいずれかのレベルで転送セキュリティを使用すると、メッセージの検査機能に影響がある点に注意してください。 機密性はメッセージが検査されないように保護し、整合性はメッセージが変更されないように保護します。|テキスト|  
|信頼性|信頼性は、転送エラーに対するエンコーダーの復元能力です。 信頼性はメッセージ層、トランスポート層、またはアプリケーション層でも提供できます。 すべての [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 標準エンコーダーは、信頼性が別の層で提供されることを前提としています。 エンコーダーは、転送エラーから回復する機能をほとんど備えていません。|なし|  
|単純さ|単純さは、エンコード仕様に対応するエンコーダーとデコーダーの作成の容易さを表します。 テキスト エンコーディングは、単純さの面で特に優れており、POX テキスト エンコーディングは SOAP 処理のサポートが不要なため、さらに優れています。|テキスト (POX)|  
|サイズ|エンコーディングによって、コンテンツに課せられるオーバーヘッドの量が決まります。 エンコードされたメッセージのサイズは、サービス操作の最大スループットに直接影響します。 バイナリ エンコーディングは、一般にテキスト エンコーディングよりサイズが小さくなります。 メッセージのサイズが優先事項である場合は、エンコーディング中にメッセージ コンテンツを圧縮することも検討してください。 ただし、圧縮を行うとメッセージの送信者と受信者の両方で処理コストが大きくなります。|2 項|  
|ストリーム|ストリーミングでは、アプリケーションはメッセージ全体が到着する前にメッセージの処理を開始できます。 ストリーミングを効果的に使用するには、受信するアプリケーションが重要なデータの到着を待つ必要をなくすために、メッセージの冒頭で重要なデータが利用可能になっている必要があります。 さらに、ストリーミングされた転送を使用するアプリケーションでは、メッセージ コンテンツに前方依存性がないように、メッセージ内のデータを順次編成していく必要があります。 多くの場合、コンテンツのストリーミングと必要最小限のサイズで転送を行うこととの間で妥協を図る必要があります。|なし|  
|サードパーティ製ツールのサポート|エンコーディングのサポート領域には、開発と診断があります。 サードパーティの開発者は、POX 形式でエンコードされたメッセージを処理するためのライブラリとツールキットに多大な投資をしています。|テキスト (POX)|  
|相互運用性|この要因は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のエンコーダーの、非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスとの相互運用性を表しています。|テキスト<br /><br /> MTOM (部分的)|  
  
メモ: バイナリ エンコーダーを使用している場合、XMLReader を作成するときに IgnoreWhitespace の設定を使用しても効果はありません。  たとえば、サービス操作内で次の操作を実行するとします。  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
IgnoreWhitespace の設定は無視されます。  
  
## <a name="compression-and-the-binary-encoder"></a>圧縮およびバイナリ エンコーダー

WCF 4.5 以降の WCF バイナリ エンコーダーでは、圧縮がサポートされます。 これにより、WCF クライアントから圧縮メッセージを送信するための gzip/deflate アルゴリズムを使用でき、さらに自己ホスト型 WCF サービスからの圧縮メッセージに応答することができます。 この機能は、HTTP トランスポートおよび TCP トランスポートの両方で圧縮を有効にします。 IIS のホスト サーバーを構成することによって、いつでも IIS でホストされる WCF サービスを有効にして圧縮された応答を送信できます。 圧縮の種類は <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> プロパティで構成されます。 このプロパティは、いずれかの <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> 列挙値に設定されます。

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
このプロパティは、binaryMessageEncodingBindingElement でのみ公開される、ため、次のようにこの機能を使用するカスタム バインディングを作成する必要があります。

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

クライアントとサービスの両方を圧縮したメッセージの送受信に同意する必要があります。 したがって、compressionFormat プロパティは、クライアントとサービスの両方の binaryMessageEncoding 要素で構成する必要があります. サービスまたはクライアントの一方で圧縮が構成され、他方で圧縮が構成されていない場合は ProtocolException がスローされます。圧縮の有効化は慎重に考慮する必要があります。 圧縮は、ネットワーク帯域幅がボトルネックになっている場合に最も効果的です。 CPU がボトルネックである場合、圧縮によりスループットが低下します。 これがアプリケーションにとってメリットがあるかどうかを確認するために、適切なテストをシミュレートされた環境で行う必要があります。  
  
## <a name="see-also"></a>関連項目

[バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)
