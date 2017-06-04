---
title: "WebResponse からの派生 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WebResponse からの派生"
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# WebResponse からの派生
<xref:System.Net.WebResponse> クラスは、.NET Framework プラグインの可能なプロトコル モデルを満たすプロトコル対応する応答を作成する基本およびメソッド プロパティを提供する抽象的な基本クラスです。  リソースのデータを要求するに <xref:System.Net.WebRequest> クラスを使用するアプリケーションは **WebResponse**の応答が表示されます。  **WebResponse** プロトコル対応その子孫は **WebResponse** クラスの抽象的なメンバを行う必要があります。  
  
 **\[WebRequest\]** のクラスは、**WebResponse** その子孫を作成する必要があります。  たとえば、<xref:System.Net.HttpWebResponse> のインスタンスは <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=fullName> または <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=fullName>を呼び出しの結果のみ作成されます。  各 **WebResponse** は、リソースの要求の結果を含み、再利用ものではありません。  
  
## ContentLength のプロパティ  
 <xref:System.Net.WebResponse.ContentLength%2A> のプロパティは <xref:System.Net.WebResponse.GetResponseStream%2A> 方法によって返されたストリームから使用可能なデータのバイト数を示します。  **\[ContentLength\]** のプロパティはサーバーが返品ヘッダーまたはメタデータ情報のバイト数を参照する; これは、要求されたリソースのデータのバイト数を自体を示します。  
  
## ContentType のプロパティ  
 <xref:System.Net.WebResponse.ContentType%2A> のプロパティは送信サーバーが格納されるデータのタイプを識別するために、セキュリティはクライアントにするように要求すると特殊な情報を提供します。  通常、これは返品データ要素の MIME のコンテンツ タイプです。  
  
## ヘッダーのプロパティ  
 <xref:System.Net.WebResponse.Headers%2A> のプロパティが応答に関連付けられているメタデータの名前と値の組み合わせのコレクション オプションが含まれます。  名前と値の組み合わせで表すことができるプロトコルが必要とするしたメタデータが **\[ヘッダー\]** のプロパティに含めることができます。  
  
 ヘッダーのメタデータを使用するに **\[ヘッダー\]** のプロパティを使用する必要はありません。  プロトコル対応のメタデータをプロパティとして公開できます。; たとえば、<xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=fullName> のプロパティは **Last\-Modified** の HTTP ヘッダーを公開します。  プロパティとしてヘッダーのメタデータを公開すると、同じプロパティが **\[ヘッダー\]** のプロパティを使用するように設定できません。  
  
## ResponseUri のプロパティ  
 <xref:System.Net.WebResponse.ResponseUri%2A> のプロパティは、実際に回答を提供したリソースの URI が含まれます。  リダイレクトをサポート プロトコルとして、**ResponseUri** が応答を作成した **\[WebRequest\]** の <xref:System.Net.WebRequest.RequestUri%2A> のプロパティと同じです。  プロトコルが要求の方向を変更することをサポートしている場合は、**ResponseUri** URI の応答が含まれます。  
  
## 原価計算方法  
 <xref:System.Net.WebResponse.Close%2A> 方法は要求と回答による接続を閉じ、応答で使用されるリソースを遵守します。  **\[閉じる\]** 方法が応答で使用されるストリームのインスタンスを閉じますが応答のベースが <xref:System.IO.Stream.Close%2A?displayProperty=fullName> のメソッドへの呼び出しによって前に閉じられたら例外を投げません。  
  
## GetResponseStream 方法  
 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法は、要求されたリソースから回答を含むストリームを返します。  回答のベースは、リソースから返されたデータのみが含まれます; 応答に含まれるヘッダーまたはメタデータをプロトコル対応するプロパティまたは **\[ヘッダー\]** のプロパティを使用してアプリケーションへの応答から削除され、公開する必要があります。  
  
 **GetResponseStream** 方法によって返されたストリームのインスタンスはアプリケーションが所有して、**WebResponse**を閉じないで決済できます。  慣例に、**\[WebResponse.Close\]** 方法を追加すると、**GetResponse**によって返されたストリームを閉じます。  
  
## 参照  
 <xref:System.Net.WebResponse>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.FileWebResponse>   
 [プラグ可能なプロトコルのプログラミング](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [WebRequest からの派生](../../../docs/framework/network-programming/deriving-from-webrequest.md)