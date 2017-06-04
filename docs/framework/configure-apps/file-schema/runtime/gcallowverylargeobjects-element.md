---
title: "&lt;gcAllowVeryLargeObjects&gt; 要素 | Microsoft Docs"
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
  - "<gcAllowVeryLargeObjects> 要素"
  - "gcAllowVeryLargeObjects 要素"
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;gcAllowVeryLargeObjects&gt; 要素
64 ビット プラットフォームで、合計サイズが 2 GB \(ギガバイト\) を超える配列を有効にします。  
  
## 構文  
  
```  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> 64 ビット プラットフォームで、合計サイズが 2 GB \(ギガバイト\) を超える配列が有効であるかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|合計サイズが 2 GB を超える配列は有効ではありません。  これは、既定の設定です。|  
|`true`|64 ビット プラットフォームで、合計サイズが 2 GB を超える配列が有効になっています。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 アプリケーション構成ファイルで次の要素を使用すると 2 GB を超えるサイズの配列が有効になりますが、オブジェクトのサイズや配列のサイズに対するその他の制限は変更されません。  
  
-   配列の要素の最大数は <xref:System.UInt32.MaxValue?displayProperty=fullName> です。  
  
-   バイト配列および 1 バイト構造体の配列の場合、単一次元の最大インデックスは 2,147,483,591 \(0x7FFFFFC7\) です。その他の種類の場合は 2,146,435,071 \(0X7FEFFFFF\) です。  
  
-   文字列およびその他の非配列オブジェクトの最大サイズは変更されません。  
  
> [!CAUTION]
>  この機能を有効にする前に、すべての配列のサイズが 2 GB よりも小さいことを前提としたアンセーフ コードがアプリケーションに含まれていないことを確認します。  たとえば、バッファーとして配列を使用するアンセーフ コードが、配列は 2 GB を超えないという前提で記述されている場合、バッファー オーバーランが発生しやすくなる可能性があります。  
  
## 使用例  
 アプリケーションでこの機能を有効にする方法を次の例に示します。  
  
```  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)