---
title: "schemeSettings の &lt;clear&gt; 要素 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# schemeSettings の &lt;clear&gt; 要素 (Uri 設定)
既存のスキーム設定をすべて消去します。  
  
## 構文  
  
```  
  
<clear/>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<schemeSettings\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキーマに対して解析される方法を指定します。|  
  
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
 スキーム設定をすべて消去してから、http スキームのパーセント記号をエンコードしたパス区切り記号をエスケープしないようにする、<xref:System.Uri> クラスで使用する構成を次のコード例に示します。  
  
```  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## 参照  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=fullName>   
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=fullName>   
 <xref:System.GenericUriParserOptions?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)