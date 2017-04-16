---
title: "ASP.NET での System.Transactions の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# ASP.NET での System.Transactions の使用
ここでは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション内で <xref:System.Transactions> を正しく使用する方法について説明します。  
  
## ASP.NET での DistributedTransactionPermission の有効化  
 <xref:System.Transactions> は、部分的に信頼された呼び出し側をサポートしており、**AllowPartiallyTrustedCallers** 属性 \(APTCA\) を使用してマークされます。<xref:System.Transactions> の信頼レベルは、<xref:System.Transactions> が公開するリソースの種類 \(システム メモリ、共有プロセス全体のリソース、システム全体のリソース、その他のリソースなど\)、およびそれらのリソースにアクセスするのに必要な信頼レベルに基づいて定義されます。 部分的に信頼された環境では、<xref:System.Transactions.DistributedTransactionPermission> が付与されていない限り、完全に信頼されていないアセンブリは、アプリケーション ドメイン内でのみトランザクションを使用できます \(この場合、保護されている唯一のリソースはシステム メモリです\)。  
  
 Microsoft 分散トランザクション コーディネーター \(MSDTC\) で管理されるようトランザクション管理がエスカレートされるたびに、<xref:System.Transactions.DistributedTransactionPermission> が要求されます。 この種のシナリオでは、プロセス全体のリソースと特にグローバルなリソースを使用します。グローバルなリソースは、MSDTC ログで予約されたスペースです。 この使用方法の例として、データベース、または供給するサービスの一部としてデータベースを使用するアプリケーションへの Web フロントエンドがあります。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] は、独自の信頼レベル セットを持ち、ポリシー ファイルを介して特定のアクセス許可セットを、これらの信頼レベルに関連付けます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md)。 Windows SDK を最初にインストールした時点では、既定の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ポリシー ファイルは <xref:System.Transactions.DistributedTransactionPermission> に関連付けられていません。 そのため、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションのトランザクションが MSDTC によって管理されるようにエスカレートされると、<xref:System.Transactions.DistributedTransactionPermission> を要求した時点で、<xref:System.Security.SecurityException> によりエスカレーションが失敗します。 部分的に信頼された [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の環境でトランザクションのエスカレーションを有効にするには、<xref:System.Data.SqlClient.SqlClientPermission> と同じ既定の信頼レベルで、<xref:System.Transactions.DistributedTransactionPermission> を付与する必要があります。 これをサポートする独自のカスタム信頼レベルとポリシー ファイルを構成するか、既定のポリシー ファイルである **Web\_hightrust.config** および **Web\_mediumtrust.config** を変更できます。  
  
 ポリシー ファイルを変更するには、System.Transactions について、**DistributedTransactionPermission** の **SecurityClass** 要素を **PolicyLevel** 要素の下の **SecurityClasses** 要素に追加し、さらに [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** の下の対応する **IPermission** 要素を追加します。 次の構成ファイルに、この例を示します。  
  
```  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
  
```  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] のセキュリティ ポリシーの[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、「[securityPolicy 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/469d8d22-d263-46bb-8400-40d8d027faba)」を参照してください。  
  
## 動的コンパイル  
 アクセス時に動的にコンパイルされる [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションで <xref:System.Transactions> をインポートして使用する場合、構成ファイルに <xref:System.Transactions> アセンブリへの参照を配置する必要があります。 具体的には、既定のルートの **Web.config** 構成ファイル、または特定の Web アプリケーションの構成ファイルの **compilation**\/**assemblies** セクションに、この参照を追加する必要があります。 次に例を示します。  
  
```  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [compilation の assemblies の add 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/602197e8-108d-4249-b752-ba2a318f75e4)」を参照してください。  
  
## 参照  
 [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md)   
 [securityPolicy 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/469d8d22-d263-46bb-8400-40d8d027faba)   
 [トランザクション管理エスカレーション ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)