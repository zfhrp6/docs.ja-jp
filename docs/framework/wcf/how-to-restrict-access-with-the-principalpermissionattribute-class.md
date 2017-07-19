---
title: "方法 : PrincipalPermissionAttribute クラスでアクセスを制限する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "PrincipalPermissionAttribute クラス"
  - "WCF, 承認"
  - "WCF, セキュリティ"
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# 方法 : PrincipalPermissionAttribute クラスでアクセスを制限する
Windows ドメイン コンピューターのリソースへのアクセスを制御することは、基本的なセキュリティ タスクです。たとえば、給与情報のような機密データは、特定のユーザーだけが表示できるようにする必要があります。ここでは、ユーザーが定義済みグループに属していることを要求することによって、メソッドへのアクセスを制限する方法について説明します。実際に動作するサンプルについては、「[サービス操作へのアクセスの承認](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)」を参照してください。  
  
 タスクは、2 つの別個の手順で構成されます。最初の手順では、グループを作成してユーザーを追加します。2 番目の手順では、グループを指定するために <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。  
  
### Windows グループを作成するには  
  
1.  **\[コンピューターの管理\]** コンソールを開きます。  
  
2.  左のパネルで、**\[ローカル ユーザーとグループ\]** をクリックします。  
  
3.  **\[グループ\]** を右クリックし、**\[新しいグループ\]** をクリックします。  
  
4.  **\[グループ名\]** ボックスに、新しいグループの名前を入力します。  
  
5.  **\[説明\]** ボックスに、新しいグループの説明を入力します。  
  
6.  **\[追加\]** をクリックして、グループに新しいメンバーを追加します。  
  
7.  自分自身をグループに追加した場合は、次のコードをテストする前に、コンピューターからいったんログオフし、再度ログオンして自分自身をグループに含める必要があります。  
  
### ユーザー メンバーシップを要求するには  
  
1.  実装されたサービス コントラクト コードを含む [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] コード ファイルを開きます。コントラクトの実装[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)」を参照してください。  
  
2.  特定のグループに制限される必要がある各メソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を適用します。<xref:System.Security.Permissions.SecurityAttribute.Action%2A> プロパティを <xref:System.Security.Permissions.SecurityAction> に設定し、<xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> プロパティをグループの名前に設定します。次に例を示します。  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をコントラクトに適用すると、<xref:System.Security.SecurityException> がスローされます。この属性はメソッド レベルにのみ適用できます。  
  
## 証明書を使用したメソッドへのアクセスの制御  
 クライアント資格情報の種類が "証明書" の場合は、`PrincipalPermissionAttribute` クラスを使用してメソッドへのアクセスを制御することもできます。そのためには、証明書のサブジェクトと拇印が必要になります。  
  
 証明書のプロパティを確認する方法については、「[方法 : MMC スナップインを使用して証明書を参照する](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)」を参照してください。拇印の値を検索する方法については、「[方法 : 証明書のサムプリントを取得する](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)」を参照してください。  
  
#### 証明書を使用してアクセスを制御するには  
  
1.  アクセスを制限するメソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。  
  
2.  属性のアクションを <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> に設定します。  
  
3.  `Name` プロパティを、サブジェクト名と証明書の拇印で構成される文字列に設定します。次の例に示すように、2 つの値をセミコロンと空白で区切ってください。  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  次の構成例に示すように、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを <xref:System.ServiceModel.Description.PrincipalPermissionMode> に設定します。  
  
    ```  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     この値を `UseAspNetRoles` に設定すると、`PrincipalPermissionAttribute` の `Name` プロパティを使用して文字列が比較されます。クライアント資格情報として証明書を使用している場合、既定では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は証明書の共通名と拇印をセミコロンで連結して、クライアントのプライマリ ID を表す一意の値が作成されます。`UseAspNetRoles` をサービスの `PrincipalPermissionMode` として設定している場合、このプライマリ ID の値と `Name` プロパティの値を比較してユーザーのアクセス権が決定されます。  
  
     また、自己ホスト型サービスを作成する場合は、次のコードに示すように、コードの <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを設定します。  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## 参照  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 <xref:System.Security.Permissions.SecurityAction>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>   
 [サービス操作へのアクセスの承認](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)   
 [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)