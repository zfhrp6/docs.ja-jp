---
title: '方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 14f7691046f9512e25006bd6cd02749eed825003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)
Windows Communication Foundation (WCF) では、X.509 証明書を使用して署名された SOAP メッセージを受信したときに既定ではことを確認、X.509 証明書が信頼された証明機関によって発行されたことです。 これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。 WCF この判断を行うためには、適切な証明書ストアに証明機関の証明書チェーンをインストールする必要があります。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>証明機関証明書チェーンをインストールするには  
  
-   各証明機関を信頼しているつもりの SOAP メッセージの受信者では、X.509 証明書の発行元から X.509 証明書を取得する WCF が構成されている証明書ストアに証明機関の証明書チェーンをインストールします。  
  
     たとえば、SOAP メッセージの受信者は、マイクロソフトによって発行された X.509 証明書を信頼しているつもりから X.509 証明書を検索する WCF が設定されている証明書ストアに、Microsoft の証明機関の証明書チェーンをインストールされて必要があります。 WCF が X.509 証明書を検索する場合に、証明書ストアは、コードまたは構成で指定できます。 これを使用してコードで指定するなど、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>メソッドまたは構成など、いくつかの方法で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)です。  
  
     Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。  
  
    1.  証明機関証明書チェーンをエクスポートします。  
  
         正確なエクスポート方法は、証明機関によって異なります。 証明機関で Microsoft 証明書サービスが実行されている場合は、選択**CA 証明書、証明書チェーン、または CRL のダウンロード**を選択し**ダウンロードの CA 証明書**です。  
  
    2.  証明機関証明書チェーンをインポートします。  
  
         Microsoft 管理コンソール (MMC: Microsoft Management Console) で、証明書スナップインを開きます。 選択から X.509 証明書を取得する証明書ストアの WCF が構成されている、**の信頼されたルート****証明機関**フォルダーです。 下にある、**信頼されたルート証明機関**フォルダーを右クリックし、**証明書**フォルダーをポイント**すべてのタスク**、順にクリック**インポート**. 手順 a. でエクスポートしたファイルを指定します。  
  
         詳細については、MMC で、証明書スナップインを使用して、次を参照してください。[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)です。  
  
## <a name="see-also"></a>関連項目  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
