---
title: "&lt;supportPortability&gt; 要素 | Microsoft Docs"
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
  - "<supportPortability> 要素"
  - "supportPortability 要素"
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;supportPortability&gt; 要素
.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。  
  
## 構文  
  
```  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|PKT|必須の属性です。<br /><br /> 対象となるアセンブリの公開キー トークンを文字列で指定します。|  
|enabled|省略可能な属性。<br /><br /> 指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|true|指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にします。  これは、既定の設定です。|  
|false|指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを無効にします。  この場合、指定したアセンブリの複数の実装をアプリケーションで参照できます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
  
## 解説  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、.NET Framework の実装と .NET Framework for Silverlight の実装のどちらかなど、.NET Framework の 2 つの実装のうちどちらでも使用できるアプリケーションが自動的にサポートされます。  特定の .NET Framework アセンブリの 2 つの実装は、アセンブリ バインダーで同等と見なされます。  一部のシナリオでは、アプリケーションの移植性を高めるためのこの機能が問題になります。  そのようなシナリオでは、`<supportPortability>` 要素を使用して、この機能を無効にすることができます。  
  
 一例として、特定の参照アセンブリの .NET Framework の実装と .NET Framework for Silverlight の実装の両方を参照する必要があるアセンブリが挙げられます。  たとえば、WPF \(Windows Presentation Foundation\) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップの実装を参照すると共に、Silverlight の実装に組み込まれている WPF のサブセットも参照する必要がある場合があります。  既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。  この要素を使用すると、既定の動作を無効にし、コンパイルを正常に実行できます。  
  
> [!IMPORTANT]
>  コンパイラから共通言語ランタイムのアセンブリ バインディング ロジックに情報を渡すには、`/appconfig` コンパイラ オプションを使用して、この要素を含む app.config ファイルの場所を指定する必要があります。  
  
## 使用例  
 .NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリについて、その両方の実装をアプリケーションで参照できるようにする例を次に示します。  `/appconfig` コンパイラ オプションを使用して、この app.config ファイルの場所を指定する必要があります。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [\/appconfig \(C\# コンパイラ オプション\)](http://msdn.microsoft.com/library/ee523958.aspx)   
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/ja-jp/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)