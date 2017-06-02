---
title: "方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF) | Microsoft Docs"
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
  - "証明書 [WCF], 証明機関証明書チェーンの指定"
  - "証明書 [WCF], 署名の検査"
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、X.509 証明書を使用して署名された SOAP メッセージを受信すると、その X.509 証明書が信頼された証明機関によって発行されたものかどうかを既定で検証します。これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれが確認されるようにするには、証明機関証明書チェーンを適切な証明書ストアにインストールする必要があります。  
  
### 証明機関証明書チェーンをインストールするには  
  
-   SOAP メッセージの受信者が信頼する必要のある X.509 証明書の発行元の各証明機関について、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の取得元として構成されている証明書ストアに、証明機関証明書チェーンをインストールします。  
  
     たとえば、SOAP メッセージの受信者がマイクロソフトによって発行された X.509 証明書を信頼する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の検索先として設定されている証明書ストアに、マイクロソフトの証明機関証明書チェーンをインストールする必要があります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が X.509 証明書を検索する証明書ストアは、コードまたは構成で指定できます。たとえば、これをコードで指定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。構成では、[\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)など、複数の方法で指定できます。  
  
     Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。  
  
    1.  証明機関証明書チェーンをエクスポートします。  
  
         正確なエクスポート方法は、証明機関によって異なります。証明機関で Microsoft 証明書サービスを実行している場合は、**\[CA 証明書、証明書チェーン、または CRL のダウンロード\]** を選択し、**\[CA 証明書のダウンロード\]** を選択します。  
  
    2.  証明機関証明書チェーンをインポートします。  
  
         Microsoft 管理コンソール \(MMC: Microsoft Management Console\) で、証明書スナップインを開きます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の取得元として構成されている証明書ストアの場合は、**\[信頼されたルート** **証明機関\]** フォルダーを選択します。**\[信頼されたルート証明機関\]** フォルダーの下の **\[証明書\]** フォルダーを右クリックし、**\[すべてのタスク\]** をポイントして、**\[インポート\]** をクリックします。手順 a. でエクスポートしたファイルを指定します。  
  
         MMC で証明書スナップインを使用する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : MMC スナップインを使用して証明書を参照する](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)」を参照してください。  
  
## 参照  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)