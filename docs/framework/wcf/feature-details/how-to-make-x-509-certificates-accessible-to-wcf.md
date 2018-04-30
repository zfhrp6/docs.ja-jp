---
title: '方法 : X.509 証明書を WCF からアクセス可能にする'
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
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77ee21074b6f1bb5a2f5bd4ee653100d3534075d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>方法 : X.509 証明書を WCF からアクセス可能にする
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] から X.509 証明書にアクセスできるようにするには、アプリケーション コードで証明書ストアの名前と場所を指定する必要があります。 特定の状況では、X.509 証明書に関連付けられた秘密キーを格納しているファイルにプロセス ID がアクセスできる必要があります。 証明書ストア内の X.509 証明書に関連付けられている秘密キーを取得するには、それを行うためのアクセス許可が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に必要になります。 既定では、所有者と System アカウントだけが証明書の秘密キーにアクセスできます。  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X.509 証明書を WCF からアクセス可能にするには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントに対して、X.509 証明書に関連付けられている秘密キーを格納しているファイルへの読み取りアクセス権を与えます。  
  
    1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に X.509 証明書の秘密キーへの読み取りアクセス権が必要かどうかを判断します。  
  
         次の表は、X.509 証明書を使用する際に秘密キーを使用できる必要があるかどうかを示しています。  
  
        |X.509 証明書の使用法|秘密キー|  
        |---------------------------|-----------------|  
        |送信 SOAP メッセージにデジタル署名する。|[はい]|  
        |受信 SOAP メッセージの署名を検証する。|×|  
        |送信 SOAP メッセージを暗号化する。|×|  
        |受信 SOAP メッセージを復号化する。|[はい]|  
  
    2.  証明書が格納されている証明書ストアの場所と名前を決定します。  
  
         証明書が格納されている証明書ストアは、アプリケーション コードまたは構成で指定します。 たとえば、次の例では、証明書が `CurrentUser` という名前の `My` 証明書ストア内に存在することを指定します。  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  証明書の秘密キーをコンピューターに配置を使用して場所を判断、 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)ツールです。  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)ツールは、証明書ストアの名前、証明書ストアの場所、およびその証明書を一意に識別するものが必要です。 このツールは、証明書のサブジェクト名または拇印を一意の識別子として受け入れます。 証明書の拇印を確認する方法の詳細については、次を参照してください。[する方法: 証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)です。  
  
         次のコード例では、 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)内の証明書の秘密キーの場所を特定するツール、`My`で格納`CurrentUser`の拇印を持つ`46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`します。  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントを確認します。  
  
         次の表は、特定のシナリオで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントの詳細を示しています。  
  
        |シナリオ|プロセス ID|  
        |--------------|----------------------|  
        |クライアント (コンソールまたは WinForms アプリケーション)|現在ログインしているユーザー|  
        |自己ホスト型のサービス|現在ログインしているユーザー|  
        |IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) または IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]) でホストされているサービス|NETWORK SERVICE|  
        |IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]) でホストされているサービス|Machine.config ファイル内の `<processModel>` 要素によって制御されます。 既定のアカウントは ASPNET です。|  
  
    5.  cacls.exe などのツールを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントに、秘密キーを格納しているファイルへの読み取りアクセス権を与えます。  
  
         次のコード例では、指定したファイルのアクセス制御リスト (ACL) を編集 (/E) して、NETWORK SERVICE アカウントにそのファイルへの読み取り (R) アクセス権を与えます。  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>関連項目  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [方法 : 証明書のサムプリントを取得する](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
