---
title: "&lt;schemeSettings&gt; 要素 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;schemeSettings&gt; 要素 (Uri 設定)
<xref:System.Uri> が特定のスキーマに対して解析される方法を指定します。  
  
## 構文  
  
```  
  
      <schemeSettings>   
</schemeSettings>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|スキーム名に対するスキーム設定を追加します。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|既存のスキーム設定をすべて消去します。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|スキーム名に対するスキーム設定を削除します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|URI \(Uniform Resource Identifier\) で表現された Web アドレスが .NET Framework によってどのように処理されるかの設定を格納します。|  
  
## 解説  
 既定では、<xref:System.Uri?displayProperty=fullName> クラスは、パスの圧縮を実行する前に、パーセント記号をエンコードしたパス区切り記号のエスケープを解除します。  これは、次のような攻撃に対するセキュリティ機構として実装されました。  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 パーセント記号をエンコードした文字を正しく処理できないモジュールにこの URI が渡されると、次のコマンドがサーバーによって実行されます。  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 このため、<xref:System.Uri?displayProperty=fullName> クラスでは、パス区切り記号のエスケープを解除してから、パスの圧縮を適用します。  上のような悪意のある URL を <xref:System.Uri?displayProperty=fullName> クラス コンストラクターに渡した場合、次の URI になります。  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセント記号をエンコードしたパス区切り記号のエスケープを解除しないように変更できます。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 http スキームのパーセント記号をエンコードしたパス区切り記号をエスケープしないようにするために、<xref:System.Uri> クラスで使用する構成を次のコード例に示します。  
  
```  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間|システム|  
|スキーマ名||  
|検証ファイル||  
|空も使用できる||  
  
## 参照  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=fullName>   
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=fullName>   
 <xref:System.GenericUriParserOptions?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)