---
title: "アクセス制御機構 | Microsoft Docs"
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
  - "アクセス制御 [WCF]"
  - "WCF セキュリティ"
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# アクセス制御機構
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、複数の方法でアクセスを制御できます。ここでは、正しい機構を選択して使用できるように、さまざまな機構について簡単に説明し、各機構を使用するタイミングに関するヒントを提供します。ここでは、アクセス テクノロジを単純なものから順に示します。最も単純なのは <xref:System.Security.Permissions.PrincipalPermissionAttribute> で、最も複雑なのは ID モデルです。  
  
 これらの機構とは別に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での委任と偽装については、「[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)」を参照してください。  
  
## PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを制限するために使用します。この属性をメソッドに適用して使用すると、特定の呼び出し元の ID や Windows グループまたは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロールでのメンバーシップを要求できます。クライアントが、X.509 証明書を使用して認証された場合は、サブジェクト名と証明書の拇印で構成されるプライマリ ID がクライアントに割り当てられています。  
  
 サービスのユーザーが常に、サービスが実行されているものと同じ Windows ドメインのメンバーである場合、サービスが実行されているコンピューター上のリソースへのアクセスを制御するには、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用します。指定したアクセス レベル \(なし、読み取り専用、または読み取りと書き込みなど\) を持つ Windows グループを簡単に作成できます。  
  
 属性の使用[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)」を参照してください。ID [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## ASP.NET メンバーシップ プロバイダー  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の機能の 1 つに、メンバーシップ プロバイダーがあります。メンバーシップ プロバイダーは、厳密にはアクセス制御機構ではありませんが、これを使用すると、サービスのエンドポイントにアクセスできる ID のセットを制限することで、サービスへのアクセスを制御できます。メンバーシップ機能には、ユーザー名\/パスワードの組み合わせを設定できるデータベースが含まれています。この組み合わせによって、Web サイトのユーザーはサイトのアカウントを確立できます。ユーザーがメンバーシップ プロバイダーを使用するサービスにアクセスするには、自分の名前とパスワードを使用してログオンする必要があります。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが認証のために使用できるように、最初にこの [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 機能を使用してデータベースを設定しておく必要があります。  
  
 また、このメンバーシップ機能を使用すると、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイトにメンバーシップ データベースが既にある場合に、同じユーザー名とパスワードで承認された同じユーザーがサービスを使用できるようになります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでのメンバーシップ プロバイダーの使用[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)」を参照してください。  
  
## ASP.NET ロール プロバイダー  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] には、ロールを使用して承認を管理する機能もあります。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを使用すると、開発者は、ユーザーのロールを作成し、各ユーザーを 1 つまたは複数のロールに割り当てることができます。メンバーシップ プロバイダーと同様に、ロールと割り当てはデータベースに格納され、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーの特定の実装によって提供されるツールを使用して設定できます。また、メンバーシップ機能と同様に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開発者は、データベースの情報を使用してサービス ユーザーをロール別に承認できます。たとえば、上記の `PrincipalPermissionAttribute` アクセス制御機構と組み合わせてロール プロバイダーを使用できます。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダー データベースが既に存在し、同じルールとユーザー割り当てのセットを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで利用する場合にも使用できます。  
  
 ロール プロバイダー機能の使用[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)」を参照してください。  
  
## 承認マネージャー  
 さらに、承認マネージャー \(AzMan\) と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを組み合わせてクライアントを承認する機能もあります。Web サービスを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] によってホストする場合は、サービスの承認が AzMan 経由で行われるように AzMan をアプリケーションに統合できます。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール マネージャーは、アプリケーション ロールの管理、ロールへのユーザーの追加と削除、およびロール メンバーシップのチェックを実行できるようにする API を提供しますが、指定されたタスクまたは操作の実行がユーザーに許可されているかどうかを照会する機能は提供しません。AzMan を使用すると、個々の操作を定義してタスクに結合できます。AZMan では、ロールのチェックだけでなく、ユーザーがタスクを実行できるかどうかをチェックすることもできます。ロールの割り当てとタスクの承認は、アプリケーションの外部で構成することも、アプリケーション内でプログラムによって実行することもできます。AzMan 管理 Microsoft 管理コンソール \(MMC: Microsoft Management Console\) スナップインにより、管理者は、ロールが実行時に実行できるタスクを変更したり、ユーザーのロール メンバーシップを管理したりできます。  
  
 また、AzMan と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーは、既存の AzMan インストールに既にアクセスでき、AzMan とロール プロバイダーの組み合わせの機能を使用してサービス ユーザーを承認する場合にも使用できます。  
  
 AzMan と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダー[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[How To: ASP.NET 2.0 で Authorization Manager \(AzMan\) を使用する方法](http://go.microsoft.com/fwlink/?LinkId=88951)」を参照してください。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでの AzMan とロール プロバイダーの使用方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)」を参照してください。  
  
## ID モデル  
 ID モデルは、クライアントを承認するためのクレームとポリシーを管理できるようにする API のセットです。ID モデルを使用すると、呼び出し元がサービスに対するそれ自体の認証に使用した資格情報に含まれるすべてのクレームを調べ、それらをサービスのポリシー セットと比較し、この比較に基づいてアクセスを許可または拒否できます。  
  
 アクセスを許可する前に、微調整と、特定の条件を設定する機能が必要な場合は、ID モデルを使用します。たとえば、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用した場合、条件は、ユーザー ID が認証され、それが特定のロールに属するということだけになります。これに対し、ID モデルを使用すると、ドキュメントの参照を許可されるにはユーザーが 18 才以上であり、有効な運転免許証を所有している必要があることを明確に示すポリシーを作成できます。  
  
 ID モデルのクレームに基づくアクセス制御の恩恵を受けることができる例として、発行済みトークンのシナリオでフェデレーション資格情報を使用する場合が挙げられます。フェデレーションと発行済みトークン[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。  
  
 ID モデル[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)」を参照してください。  
  
## 参照  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 [方法 : PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)   
 [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)   
 [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)