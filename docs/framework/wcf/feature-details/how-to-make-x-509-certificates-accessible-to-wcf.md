---
title: "方法 : X.509 証明書を WCF からアクセス可能にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d4dee17b60d83f6019eda3f6431813911d3468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="bac66-102">方法 : X.509 証明書を WCF からアクセス可能にする</span><span class="sxs-lookup"><span data-stu-id="bac66-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="bac66-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] から X.509 証明書にアクセスできるようにするには、アプリケーション コードで証明書ストアの名前と場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bac66-103">To make an X.509 certificate accessible to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], application code must specify the certificate store name and location.</span></span> <span data-ttu-id="bac66-104">特定の状況では、X.509 証明書に関連付けられた秘密キーを格納しているファイルにプロセス ID がアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bac66-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="bac66-105">証明書ストア内の X.509 証明書に関連付けられている秘密キーを取得するには、それを行うためのアクセス許可が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に必要になります。</span><span class="sxs-lookup"><span data-stu-id="bac66-105">To obtain the private key associated with an X.509 certificate in a certificate store, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must have permission to do so.</span></span> <span data-ttu-id="bac66-106">既定では、所有者と System アカウントだけが証明書の秘密キーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bac66-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="bac66-107">X.509 証明書を WCF からアクセス可能にするには</span><span class="sxs-lookup"><span data-stu-id="bac66-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="bac66-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントに対して、X.509 証明書に関連付けられている秘密キーを格納しているファイルへの読み取りアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="bac66-108">Give the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="bac66-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に X.509 証明書の秘密キーへの読み取りアクセス権が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bac66-109">Determine whether [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="bac66-110">次の表は、X.509 証明書を使用する際に秘密キーを使用できる必要があるかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="bac66-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="bac66-111">X.509 証明書の使用法</span><span class="sxs-lookup"><span data-stu-id="bac66-111">X.509 certificate use</span></span>|<span data-ttu-id="bac66-112">秘密キー</span><span class="sxs-lookup"><span data-stu-id="bac66-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="bac66-113">送信 SOAP メッセージにデジタル署名する。</span><span class="sxs-lookup"><span data-stu-id="bac66-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="bac66-114">はい</span><span class="sxs-lookup"><span data-stu-id="bac66-114">Yes</span></span>|  
        |<span data-ttu-id="bac66-115">受信 SOAP メッセージの署名を検証する。</span><span class="sxs-lookup"><span data-stu-id="bac66-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="bac66-116">いいえ</span><span class="sxs-lookup"><span data-stu-id="bac66-116">No</span></span>|  
        |<span data-ttu-id="bac66-117">送信 SOAP メッセージを暗号化する。</span><span class="sxs-lookup"><span data-stu-id="bac66-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="bac66-118">いいえ</span><span class="sxs-lookup"><span data-stu-id="bac66-118">No</span></span>|  
        |<span data-ttu-id="bac66-119">受信 SOAP メッセージを復号化する。</span><span class="sxs-lookup"><span data-stu-id="bac66-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="bac66-120">はい</span><span class="sxs-lookup"><span data-stu-id="bac66-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="bac66-121">証明書が格納されている証明書ストアの場所と名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="bac66-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="bac66-122">証明書が格納されている証明書ストアは、アプリケーション コードまたは構成で指定します。</span><span class="sxs-lookup"><span data-stu-id="bac66-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="bac66-123">たとえば、次の例では、証明書が `CurrentUser` という名前の `My` 証明書ストア内に存在することを指定します。</span><span class="sxs-lookup"><span data-stu-id="bac66-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="bac66-124">証明書の秘密キーをコンピューターに配置を使用して場所を判断、 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)ツールです。</span><span class="sxs-lookup"><span data-stu-id="bac66-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="bac66-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)ツールは、証明書ストアの名前、証明書ストアの場所、およびその証明書を一意に識別するものが必要です。</span><span class="sxs-lookup"><span data-stu-id="bac66-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="bac66-126">このツールは、証明書のサブジェクト名または拇印を一意の識別子として受け入れます。</span><span class="sxs-lookup"><span data-stu-id="bac66-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bac66-127">証明書の拇印を特定するを参照してください方法[する方法: 証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)です。</span><span class="sxs-lookup"><span data-stu-id="bac66-127"> how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="bac66-128">次のコード例では、 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)内の証明書の秘密キーの場所を特定するツール、`My`で格納`CurrentUser`の拇印を持つ`46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`します。</span><span class="sxs-lookup"><span data-stu-id="bac66-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="bac66-129">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="bac66-129">Determine the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under.</span></span>  
  
         <span data-ttu-id="bac66-130">次の表は、特定のシナリオで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントの詳細を示しています。</span><span class="sxs-lookup"><span data-stu-id="bac66-130">The following table details the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="bac66-131">シナリオ</span><span class="sxs-lookup"><span data-stu-id="bac66-131">Scenario</span></span>|<span data-ttu-id="bac66-132">プロセス ID</span><span class="sxs-lookup"><span data-stu-id="bac66-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="bac66-133">クライアント (コンソールまたは WinForms アプリケーション)</span><span class="sxs-lookup"><span data-stu-id="bac66-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="bac66-134">現在ログインしているユーザー</span><span class="sxs-lookup"><span data-stu-id="bac66-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="bac66-135">自己ホスト型のサービス</span><span class="sxs-lookup"><span data-stu-id="bac66-135">Service that is self-hosted.</span></span>|<span data-ttu-id="bac66-136">現在ログインしているユーザー</span><span class="sxs-lookup"><span data-stu-id="bac66-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="bac66-137">IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) または IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]) でホストされているサービス</span><span class="sxs-lookup"><span data-stu-id="bac66-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="bac66-138">NETWORK SERVICE</span><span class="sxs-lookup"><span data-stu-id="bac66-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="bac66-139">IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]) でホストされているサービス</span><span class="sxs-lookup"><span data-stu-id="bac66-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="bac66-140">Machine.config ファイル内の `<processModel>` 要素によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="bac66-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="bac66-141">既定のアカウントは ASPNET です。</span><span class="sxs-lookup"><span data-stu-id="bac66-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="bac66-142">cacls.exe などのツールを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実行されているアカウントに、秘密キーを格納しているファイルへの読み取りアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="bac66-142">Grant read access to the file that contains the private key to the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="bac66-143">次のコード例では、指定したファイルのアクセス制御リスト (ACL) を編集 (/E) して、NETWORK SERVICE アカウントにそのファイルへの読み取り (R) アクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="bac66-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="bac66-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="bac66-144">See Also</span></span>  
 [<span data-ttu-id="bac66-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bac66-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="bac66-146">方法: 証明書のサムプリントの取得</span><span class="sxs-lookup"><span data-stu-id="bac66-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="bac66-147">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="bac66-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
