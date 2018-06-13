---
title: 'Windows Communication Foundation 導入の準備: 将来的な統合の容易化'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489597"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation 導入の準備: 将来的な統合の容易化
現在 ASP.NET を使用して WCF を使用して、将来を予測して、このトピック指針を WCF アプリケーションと共に、新しい ASP.NET Web サービスが動作することを確認します。  
  
## <a name="general-recommendations"></a>一般的な推奨事項  
 ASP.NET 2.0 を使用して、すべての新規サービスを作成します。 こうすることで、拡張および強化された新バージョンの機能にアクセスできます。 ただし、同じアプリケーションで WCF コンポーネントと共に、ASP.NET 2.0 コンポーネントを使用する可能性はこともできます。  
  
## <a name="protocols"></a>プロトコル  
 WS-I Basic Profile 1.1 への準拠を検証するには、次のように ASP.NET 2.0 の新機能を使用します。  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WS に準拠する ASP.NET Web サービスのバインド、定義済みの WCF を使用して WCF クライアントと相互運用可能な基本プロファイル 1.1 なります<xref:System.ServiceModel.BasicHttpBinding>です。  
  
## <a name="service-development"></a>サービスの開発  
 SOAPAction HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドにルーティングする場合は、<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性の使用を避けます。 WCF では、メッセージのルーティングの SOAPAction HTTP ヘッダーを使用します。  
  
## <a name="data-representation"></a>データ表現  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。 ASP.NET Web サービスで使用するためのデータ型を定義する、今後の予定の導入 WCF で、次の操作を行います。  
  
1.  XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
2.  <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。 .NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
 この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。 ASP.NET Web サービスがメッセージで使用される型は引き出す、他の利点は、WCF アプリケーションでパフォーマンスの向上は入力が、WCF アプリケーションでデータ コントラクトとして処理することができます。  
  
## <a name="security"></a>セキュリティ  
 インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。 WCF クライアントでは、そのサポートしていません。 保護されるように、サービスに必要な場合は、これらのオプションが豊富なは、標準プロトコルに基づいているため、WCF が提供するオプションを使用します。  
  
## <a name="see-also"></a>関連項目  
 [Windows Communication Foundation の採用: 将来の移行の簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
