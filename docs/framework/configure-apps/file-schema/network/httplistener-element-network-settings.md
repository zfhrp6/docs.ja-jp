---
title: "&lt;httpListener&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;httpListener&gt; 要素 (ネットワーク設定)
<xref:System.Net.HttpListener> クラスで使用されるパラメーターをカスタマイズします。  
  
## 構文  
  
```  
  
      <httpListener  
  unescapeRequestUrl ="true|false"  
/>  
```  
  
## 型  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|unescapeRequestUrl|<xref:System.Net.HttpListener> インスタンスが変換された URI ではなくエスケープされていない生の URI を使用するかどうかを示すブール値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## 解説  
 **unescapeRequestUrl** 属性は、変換された URI ではなくエスケープされていない生の URI を <xref:System.Net.HttpListener> で使用するかどうかを示します。変換された URI では、パーセント記号をエンコードした値はすべて変換され、その他の正規化手順が実行されます。  
  
 <xref:System.Net.HttpListener> インスタンスは `http.sys` サービスを通じて要求を受け取ると、`http.sys` から渡された URI 文字列のインスタンスを作成し、そのインスタンスを <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=fullName> プロパティとして公開します。  
  
 `http.sys` サービスでは、次の 2 つの要求 URI 文字列を公開します。  
  
-   生の URI  
  
-   変換された URI  
  
 生の URI は、HTTP 要求の要求行に指定されている <xref:System.Uri?displayProperty=fullName> です。  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 前の要求の `http.sys` から渡される生の URI は、"\/path\/" です。  これは、ネットワーク上で送信された HTTP 動詞の後に続く文字列を表します。  
  
 `http.sys` サービスでは、HTTP 要求行および Host ヘッダーに指定されている URI を使用して要求の転送先となる元のサーバーを特定することによって、要求に指定されている情報から、変換された URI を作成します。  この処理は、要求の情報と一連の登録済み URI プレフィックスとを比較することで行われます。  HTTP Server SDK のドキュメントでは、この変換された URI を HTTP\_COOKED\_URL 構造体と呼びます。  
  
 要求と登録済み URI プレフィックスとを比較できるようにするためには、要求の正規化をいくつか行う必要があります。  上のサンプルでは、変換された URI は次のようになります。  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` サービスでは、<xref:System.Uri.Host%2A?displayProperty=fullName> プロパティ値と要求行の文字列を結合して、変換された URI を作成します。  また、`http.sys` と <xref:System.Uri?displayProperty=fullName> クラスでは、次の処理も行います。  
  
-   パーセント記号をエンコードしたすべての値のエスケープを解除します。  
  
-   パーセント記号をエンコードした非 ASCII 文字を UTF\-16 文字表現に変換します。  UTF\-8 文字および ANSI\/DBCS 文字も Unicode 文字 \(%uXXXX 形式を使用した Unicode エンコーディング\) と同様にサポートされることに注意してください。  
  
-   パスの圧縮など、その他の正規化手順を実行します。  
  
 パーセント記号をエンコードした値に使用されているエンコーディングに関する情報は要求に含まれていないため、パーセント記号をエンコードした値を解析するだけでは、正しいエンコーディングを判断できない場合があります。  
  
 そのため、`http.sys` には、次に示すように、この処理を変更するためのレジストリ キーが 2 つ用意されています。  
  
|レジストリ キー|既定値|説明|  
|--------------|---------|--------|  
|EnableNonUTF8|1|ゼロの場合、`http.sys` は UTF\-8 エンコードの URL のみ受け入れます。<br /><br /> ゼロ以外の場合、`http.sys` は要求で ANSI エンコードの URL または DBCS エンコードの URL も受け入れます。|  
|FavorUTF8|1|ゼロ以外の場合、`http.sys` は常に最初に URL を UTF\-8 としてデコードしようとします。その変換が失敗した場合、EnableNonUTF8 がゼロ以外のときは、ANSI または DBCS としてデコードしようとします。<br /><br /> ゼロ \(かつ EnableNonUTF8 がゼロ以外\) の場合、`http.sys` は URL を ANSI または DBCS としてデコードしようとします。失敗した場合は、UTF\-8 変換を試行します。|  
  
 <xref:System.Net.HttpListener> は要求を受け取ると、`http.sys` からの変換された URI を <xref:System.Net.HttpListenerRequest.Url%2A> プロパティへの入力として使用します。  
  
 URI では文字と数字以外の文字 \(記号など\) をサポートする必要があります。  例を次に示します。この URI は、顧客番号 "1\/3812" の顧客情報を取得するために使用するものです。  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Uri のパーセント記号をエンコードしたスラッシュに注目してください \(%2F\)。  この場合、スラッシュ文字はデータを表し、パス区切り記号ではないため、この処理は必要です。  
  
 この文字列をそのまま Uri コンストラクターに渡すと、次の URI になります。  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 パスはセグメントに分割され、次の要素になります。  
  
 `Customer('1`  
  
 `3812')`  
  
 これでは、要求の送信元の意図とは異なります。  
  
 **unescapeRequestUrl** 属性が **false** に設定されている場合、<xref:System.Net.HttpListener> は要求を受け取ると、`http.sys` からの変換された URI ではなく生の URI を <xref:System.Net.HttpListenerRequest.Url%2A> プロパティへの入力として使用します。  
  
 **unescapeRequestUrl** 属性の既定値は **true** です。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> プロパティを使用すると、適用可能な構成ファイルから **unescapeRequestUrl** 属性の現在の値を取得できます。  
  
## 使用例  
 要求を受け取ったときに、`http.sys` からの変換された URI ではなく生の URI を <xref:System.Net.HttpListenerRequest.Url%2A> プロパティへの入力として使用するように、<xref:System.Net.HttpListener> クラスを構成する方法を次のコード例に示します。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間|System.Net|  
|スキーマ名||  
|検証ファイル||  
|空も使用できる||  
  
## 参照  
 <xref:System.Net.Configuration.HttpListenerElement>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerRequest.Url%2A>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)