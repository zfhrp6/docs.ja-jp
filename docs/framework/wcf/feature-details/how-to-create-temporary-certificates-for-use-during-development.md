---
title: '方法 : 開発中に使用する一時的な証明書を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 8310e7c465d0e3494482b6a38a7b2a67b67ae842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495368"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>方法 : 開発中に使用する一時的な証明書を作成する
セキュリティで保護されたサービスまたは Windows Communication Foundation (WCF) を使用してクライアントを開発する場合、資格情報として使用する X.509 証明書を指定する必要があります。 証明書は通常、単独ではなく、いくつもの証明書が信頼チェーンとしてつながった形で存在しており、その最上位に位置するルート証明機関の証明書は、各コンピューターの [信頼されたルート証明機関] の証明書ストアに格納されています。 証明書を調べて順に信頼チェーンをたどっていくと、たとえば所属する会社や事業部門が運営する、ルート証明機関に到達します。 開発時にこの過程をエミュレートするためには、セキュリティ要件を満たす 2 種類の証明書を作る必要があります。 1 つは自己署名証明書で、[信頼されたルート証明機関] の証明書ストアに配置します。もう 1 つは、先の自己署名証明書を使って署名を施した証明書で、[ローカル コンピューター] の [個人] ストア、または [現在のユーザー] の [個人] ストアに配置します。 ここでは、 [SDK に付属する](http://go.microsoft.com/fwlink/?LinkId=248185)証明書作成ツール (MakeCert.exe) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] を使用して、これら 2 つの証明書を作成する手順を示します。  
  
> [!IMPORTANT]
>  証明書作成ツールによって作成された証明書は、テスト目的にのみ使用できます。 実際にサービスやクライアントを業務に使用する際には、証明機関から取得した、適切な証明書が必要です。 所属する会社が運営している [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 証明書サーバー、または専門の第三者機関から取得してください。  
>   
>  既定では、 [Makecert.exe (証明書作成ツール)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)がルート証明機関と呼ばれる証明書を作成"Root Agency **"。** というルート証明機関の証明書を作成します。"Root Agency" は、[信頼されたルート証明機関] の証明書ストアに含まれていないため、作成された証明書はセキュリティで保護されません。 そこで自己署名証明書を作り、[信頼されたルート証明機関] の証明書ストアに置くことにより、実際の運用環境をより忠実にシミュレートする開発環境を構築できます。  
  
 作成して、証明書の使用に関する詳細については、次を参照してください。[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。 詳細については、資格情報として証明書を使用して、次を参照してください。 [Services のセキュリティ保護とクライアント](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)です。 Microsoft Authenticode テクノロジの使用方法については、「 [Authenticode Overviews and Tutorials (Authenticode の概要とチュートリアル)](http://go.microsoft.com/fwlink/?LinkId=88919)」を参照してください。  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>自己署名ルート証明書を作成して秘密キーをエクスポートするには  
  
1.  次のスイッチを指定して MakeCert.exe ツールを使用します。  
  
    1.  `-n` `subjectName`。 サブジェクト名を指定します。 命名規則では、サブジェクト名の前に、"Common Name" を示す "CN = " を付加します。  
  
    2.  `-r`。 証明書が自己署名されるように指定します。  
  
    3.  `-sv` `privateKeyFile`。 秘密キーを書き出すファイルを指定します。  
  
     たとえば次のコマンドを実行すると、サブジェクト名を "CN=TempCA" とした自己署名証明書が作成されます。  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     秘密キーを保護するためのパスワードを入力するように求められます。 このパスワードは、このルート証明書によって署名された証明書を作成する際に必要になります。  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>ルート証明書によって署名された新しい証明書を作成するには  
  
1.  次のスイッチを指定して MakeCert.exe ツールを使用します。  
  
    1.  `-sk` `subjectKey`。 秘密キーを格納する、サブジェクトのキー コンテナーの位置を指定します。 キー コンテナーが存在しない場合は、作成されます。 -sk も -sv も指定しなかった場合、既定で JoeSoft という名前のキー コンテナーが作成されます。  
  
    2.  `-n` `subjectName`。 サブジェクト名を指定します。 命名規則では、サブジェクト名の前に、"Common Name" を示す "CN = " を付加します。  
  
    3.  `-iv` `issuerKeyFile`。 発行元の秘密キー ファイルを指定します。  
  
    4.  `-ic` `issuerCertFile`。 発行元の証明書の位置を指定します。  
  
     たとえば、次のコマンドを実行すると、サブジェクト名が `TempCA` で、発行元の秘密キーを使用する証明書が作成されます。ルート証明機関 `"CN=SignedByCA"` の証明書を使って署名されます。  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>信頼されたルート証明機関の証明書ストアに証明書をインストールする  
 作成された自己署名証明書は、[信頼されたルート証明機関] の証明書ストアにインストールできます。 この証明書で署名された証明書は、この時点で信頼できるものと見なされるようになります。 したがって、この証明書が不要になった場合は、直ちに証明書ストアから削除してください。 この証明書を削除すると、それを使って署名した証明書は認証されなくなります。 ルート証明機関の証明書は、必要に応じて一連の証明書を有効化する手段の 1 つにすぎません。 たとえばピアツーピア アプリケーションの場合、証明書が提示されれば相手の識別情報を信頼できるので、ルート証明機関は必要ないのが普通です。  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>自己署名証明書を信頼されたルート証明機関としてインストールするには  
  
1.  証明書スナップインを開きます。 詳細については、次を参照してください。[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)です。  
  
2.  証明書の格納先となる、 **[ローカル コンピューター]** または **[現在のユーザー]** のフォルダーを開きます。  
  
3.  **[信頼されたルート証明機関]** フォルダーを開きます。  
  
4.  **[証明書]** フォルダーを右クリックして、 **[すべてのタスク]** メニューの **[インポート]** を実行します。  
  
5.  ウィザード画面が開くので、その指示に従って TempCa.cer を証明書ストアにインポートしてください。  
  
## <a name="using-certificates-with-wcf"></a>WCF で証明書を使用する  
 一時的な証明書を設定したら、それを使用して、クライアント資格情報の種類として証明書を指定する WCF ソリューションを開発できます。 たとえば、次の XML 構成では、メッセージ セキュリティを設定して、クライアント資格情報の種類として証明書を指定しています。  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>クライアント資格情報の種類として証明書を指定するには  
  
-   サービスの構成ファイルで、次の XML を使用して、セキュリティ モードをメッセージに、クライアント資格情報の種類を証明書に設定します。  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 クライアントの構成ファイルで、証明書は、ユーザーのストアにあり、SubjectName フィールドの値「"cohowinery という」を検索することで見つかることを指定するのに次の XML を使用します。  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 WCF での証明書の使用に関する詳細については、「 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 一時的なルート証明書は、不要になったら **[信頼されたルート証明機関]** フォルダーや **[個人]** フォルダーから確実に削除してください。削除するには、証明書を右クリックし、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [方法 : MMC スナップインを使用して証明書を参照する](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
