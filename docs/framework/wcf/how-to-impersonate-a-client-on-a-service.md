---
title: "方法 : サービスでクライアントに偽装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, 偽装"
  - "偽装"
  - "WCF, セキュリティ"
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# 方法 : サービスでクライアントに偽装する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスでクライアントを偽装すると、サービスはクライアントの代理としてアクションを実行できます。 コンピューター上のディレクトリやファイルへのアクセス、または SQL Server データベースへのアクセスなど、アクセス制御リスト \(ACL\) のチェックを受けるアクションでは、ACL のチェックがクライアントのユーザー アカウントに対して行われます。 ここでは、Windows ドメインのクライアントで、クライアント偽装レベルを設定できるようにするために必要な基本的な手順について説明します。 このパターンの実施例については、「[クライアントの偽装](../../../docs/framework/wcf/samples/impersonating-the-client.md)」を参照してください。 クライアントの偽装の[!INCLUDE[crabout](../../../includes/crabout-md.md)]については、「[委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)」を参照してください。  
  
> [!NOTE]
>  クライアントとサービスが同じコンピューター上で実行されており、クライアントがシステム アカウント \(`Local System` や `Network Service` など\) で実行されているときに、ステートレスなセキュリティ コンテキスト トークンを使用してセキュリティで保護されたセッションを確立した場合、クライアントを偽装することはできません。 通常、WinForms アプリケーションやコンソール アプリケーションは、現在ログインしているアカウントで実行されるため、既定でそのアカウントを偽装できます。 ただし、クライアントが [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページであり、そのページが [!INCLUDE[iis601](../../../includes/iis601-md.md)] または IIS 7.0 でホストされている場合、既定では、クライアントは `Network Service` アカウントで実行されます。 セキュリティで保護されたセッションをサポートするシステム提供のすべてのバインディングは、ステートフルなセキュリティ コンテキスト トークンを既定で使用します。 ただし、クライアントが [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページであり、ステートフルなセキュリティ コンテキスト トークンを使用する、セキュリティで保護されたセッションを使用している場合は、クライアントを偽装できません。 セキュリティで保護されたセッションでのステートフルなセキュリティ コンテキスト トークンの使用方法[!INCLUDE[crabout](../../../includes/crabout-md.md)]のについては、「[方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)」を参照してください。  
  
### サービスにキャッシュされた Windows トークンでクライアントの偽装を有効にするには  
  
1.  サービスを作成します。 この基本的な手順のチュートリアルについては、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
2.  Windows 認証を使用してセッションを作成するバインディング \(<xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.WSHttpBinding> など\) を使用します。  
  
3.  サービスのインターフェイスの実装を作成するときには、クライアントの偽装を必要とするメソッドに <xref:System.ServiceModel.OperationBehaviorAttribute> クラスを適用します。<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> プロパティを <xref:System.ServiceModel.ImpersonationOption> に設定します。  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### クライアントに許可される偽装レベルを設定するには  
  
1.  [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービス クライアント コードを作成します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)。  
  
2.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントの作成後、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> クラスの <xref:System.ServiceModel.Security.WindowsClientCredential> プロパティを <xref:System.Security.Principal.TokenImpersonationLevel> 列挙値の 1 つに設定します。  
  
    > [!NOTE]
    >  <xref:System.Security.Principal.TokenImpersonationLevel> を使用するには、ネゴシエート Kerberos 認証 \(*"マルチレッグ"* Kerberos または *"マルチステップ"* Kerberos と呼ぶこともあります\) を使用する必要があります。 これを実装する方法については、「[セキュリティのベスト プラクティス](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)」を参照してください。  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## 参照  
 <xref:System.ServiceModel.OperationBehaviorAttribute>   
 <xref:System.Security.Principal.TokenImpersonationLevel>   
 [クライアントの偽装](../../../docs/framework/wcf/samples/impersonating-the-client.md)   
 [委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)