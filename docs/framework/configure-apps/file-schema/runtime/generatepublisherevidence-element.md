---
title: "&lt;generatePublisherEvidence&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<generatePublisherEvidence> 要素"
  - "generatePublisherEvidence 要素"
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;generatePublisherEvidence&gt; 要素
ランタイムでコード アクセス セキュリティ \(CAS: Code Access Security\) 用の <xref:System.Security.Policy.Publisher> 証拠を作成するかどうかを指定します。  
  
## 構文  
  
```  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムで <xref:System.Security.Policy.Publisher> 証拠を作成するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|<xref:System.Security.Policy.Publisher> 証拠を作成しません。|  
|`true`|<xref:System.Security.Policy.Publisher> 証拠を作成します。  これは、既定の設定です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、この要素はアセンブリの読み込み時間に影響を与えません。  詳細については、「[セキュリティの変更点](../../../../../docs/framework/security/security-changes.md)」のセキュリティ ポリシーの簡略化に関するセクションを参照してください。  
  
 共通言語ランタイム \(CLR: Common Language Runtime\) は、アセンブリの <xref:System.Security.Policy.Publisher> 証拠を作成するために、読み込み時に Authenticode 署名を検証します。  ただし、既定では、ほとんどのアプリケーションは <xref:System.Security.Policy.Publisher> 証拠を必要としません。  標準的な CAS ポリシーは、<xref:System.Security.Policy.PublisherMembershipCondition> に依存しません。  コンピューター上でカスタム CAS ポリシーを使用してアプリケーションを実行する場合や、部分信頼環境で <xref:System.Security.Permissions.PublisherIdentityPermission> を実現するための要求への適合を意図する場合を除き、起動時に発行者の署名の検証に関連する不要な処理を実行することは避けることが必要です \(ID アクセス許可の要求は、完全信頼環境下では必ず成功します\)。  
  
> [!NOTE]
>  起動時のパフォーマンスを向上させることを目的に、サービスで `<generatePublisherEvidence>` 要素を使用することをお勧めします。この要素は、タイムアウトの原因になる遅延や、サービス開始のキャンセルを回避することにも役立ちます。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## 使用例  
 次に、`<generatePublisherEvidence>` 要素を使用してアプリケーションの CAS 発行者ポリシー チェックを無効にする方法について説明します。  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)