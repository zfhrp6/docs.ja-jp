---
title: "方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ea15e8fe9580f561eedf048ed2aaf2e2ed248f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、X.509 証明書を使用して署名された SOAP メッセージを受信すると、その X.509 証明書が信頼された証明機関によって発行されたものかどうかを既定で検証します。 これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれを確認するには、証明機関証明書チェーンを適切な証明書ストアにインストールする必要があります。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>証明機関証明書チェーンをインストールするには  
  
-   SOAP メッセージの受信者が信頼する必要のある X.509 証明書の発行元の各証明機関について、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の取得元として構成されている証明書ストアに、証明機関証明書チェーンをインストールします。  
  
     たとえば、SOAP メッセージの受信者がマイクロソフトによって発行された X.509 証明書を信頼する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の検索先として設定されている証明書ストアに、マイクロソフトの証明機関証明書チェーンをインストールする必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が X.509 証明書を検索する証明書ストアは、コードまたは構成で指定できます。 これを使用してコードで指定するなど、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>メソッドまたは構成など、いくつかの方法で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)です。  
  
     Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。  
  
    1.  証明機関証明書チェーンをエクスポートします。  
  
         正確なエクスポート方法は、証明機関によって異なります。 証明機関で Microsoft 証明書サービスが実行されている場合は、選択**CA 証明書、証明書チェーン、または CRL のダウンロード**を選択し**ダウンロードの CA 証明書**です。  
  
    2.  証明機関証明書チェーンをインポートします。  
  
         Microsoft 管理コンソール (MMC: Microsoft Management Console) で、証明書スナップインを開きます。 証明書のストアが[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]選択から X.509 証明書を取得するように構成、**の信頼されたルート****証明機関**フォルダーです。 下にある、**信頼されたルート証明機関**フォルダーを右クリックし、**証明書**フォルダーをポイント**すべてのタスク**、順にクリック**インポート**. 手順 a. でエクスポートしたファイルを指定します。  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]MMC では、証明書スナップインを使用して参照してください[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)です。  
  
## <a name="see-also"></a>参照  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
