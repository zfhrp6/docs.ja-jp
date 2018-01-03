---
title: "ASP.NET での System.Transactions の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caa0f8cc5b98ae50e1c9d2da716dd03eb5cb4565
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET での System.Transactions の使用
ここでは、 <xref:System.Transactions> アプリケーション内で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を正しく使用する方法について説明します。  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET での DistributedTransactionPermission の有効化  
 <xref:System.Transactions> は、部分的に信頼された呼び出し側をサポートしており、 **AllowPartiallyTrustedCallers** 属性 (APTCA) を使用してマークされます。 <xref:System.Transactions> の信頼レベルは、 <xref:System.Transactions> が公開するリソースの種類 (システム メモリ、共有プロセス全体のリソース、システム全体のリソース、その他のリソースなど)、およびそれらのリソースにアクセスするのに必要な信頼レベルに基づいて定義されます。 部分的に信頼された環境では、 <xref:System.Transactions.DistributedTransactionPermission>が付与されていない限り、完全に信頼されていないアセンブリは、アプリケーション ドメイン内でのみトランザクションを使用できます (この場合、保護されている唯一のリソースはシステム メモリです)。  
  
 Microsoft 分散トランザクション コーディネーター (MSDTC) で管理されるようトランザクション管理がエスカレートされるたびに、<xref:System.Transactions.DistributedTransactionPermission> が要求されます。 この種のシナリオでは、プロセス全体のリソースと特にグローバルなリソースを使用します。グローバルなリソースは、MSDTC ログで予約されたスペースです。 この使用方法の例として、データベース、または供給するサービスの一部としてデータベースを使用するアプリケーションへの Web フロントエンドがあります。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] は、独自の信頼レベル セットを持ち、ポリシー ファイルを介して特定のアクセス許可セットを、これらの信頼レベルに関連付けます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ASP.NET 信頼レベルとポリシー ファイル](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)です。 Windows SDK を最初にインストールした時点では、既定の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ポリシー ファイルは <xref:System.Transactions.DistributedTransactionPermission>に関連付けられていません。 そのため、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションのトランザクションが MSDTC によって管理されるようにエスカレートされると、 <xref:System.Security.SecurityException> を要求した時点で、 <xref:System.Transactions.DistributedTransactionPermission>によりエスカレーションが失敗します。 部分的に信頼された [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の環境でトランザクションのエスカレーションを有効にするには、 <xref:System.Transactions.DistributedTransactionPermission> と同じ既定の信頼レベルで、 <xref:System.Data.SqlClient.SqlClientPermission>を付与する必要があります。 これをサポートする独自のカスタム信頼レベルとポリシー ファイルを構成するか、既定のポリシー ファイルである **Web_hightrust.config** および **Web_mediumtrust.config**を変更できます。  
  
 ポリシー ファイルを変更するには追加、 **SecurityClass**要素**DistributedTransactionPermission**を**SecurityClasses**要素の下、 **PolicyLevel**要素を対応する追加**IPermission**要素の下、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** System.Transactions についてです。 次の構成ファイルに、この例を示します。  
  
```xml  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] については、「 [securityPolicy 要素 (ASP.NET 設定スキーマ)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)が付与されていない限り、完全に信頼されていないアセンブリは、アプリケーション ドメイン内でのみトランザクションを使用できます (この場合、保護されている唯一のリソースはシステム メモリです)。  
  
## <a name="dynamic-compilation"></a>動的コンパイル  
 アクセス時に動的にコンパイルされる <xref:System.Transactions> アプリケーションで [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインポートして使用する場合、構成ファイルに <xref:System.Transactions> アセンブリへの参照を配置する必要があります。 具体的には、既定のルートの **Web.config**/**compilation** / **assemblies** セクションに、この参照を追加する必要があります。 次に例を示します。  
  
```xml  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][アセンブリのコンパイル (ASP.NET 設定スキーマ) の要素を追加](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4)です。  
  
## <a name="see-also"></a>参照  
 [ASP.NET の信頼レベルとポリシー ファイル](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy 要素 (ASP.NET 設定スキーマ)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)  
 [トランザクション管理のエスカレーション](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
