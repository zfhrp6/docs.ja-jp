---
title: "方法: WebRequest でインターネットとの通信にプロキシを使用できるようにする | Microsoft Docs"
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
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 方法: WebRequest でインターネットとの通信にプロキシを使用できるようにする
この例では、プロキシを使用することをインターネットと通信するために <xref:System.Net.WebRequest> を使用するグローバルなプロキシ インスタンスを作成します。  たとえば、プロキシ サーバーが `webproxy` というと、ポート 80 の通信と、標準の HTTP ポートとします。  
  
## 使用例  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **\[System.Net\]** の名前空間への参照。  
  
## 参照  
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)   
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)