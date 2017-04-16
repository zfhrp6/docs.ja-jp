---
title: "Cert2spc.exe (ソフトウェア発行元証明書テスト ツール) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "Cert2spc.exe"
  - "証明書, ソフトウェア発行元の証明書"
  - "ソフトウェア発行元証明書"
  - "ソフトウェア発行元証明書テスト ツール"
  - "SPC"
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)
ソフトウェア発行元証明書テスト ツールは、1 つ以上の X.509 証明書からソフトウェア発行元証明書 \(SPC: Software Publisher's Certificate\) を作成します。  Cert2spc.exe はテスト専用のツールです。  有効な SPC は、VeriSign や Thawte などの証明書発行機関から入手できます。  X.509 証明書の作成の詳細については、「[Makecert.exe \(証明書作成ツール\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)」を参照してください。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。  このツールを実行するには、開発者コマンド プロンプト \(または、Windows 7 の Visual Studio コマンド プロンプト\) を使用します。  詳細については、「[コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトに次のように入力します。  
  
## 構文  
  
```  
  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### パラメーター  
  
|引数|説明|  
|--------|--------|  
|`certN.cer`|SPC ファイルに組み込む X.509 証明書の名前。  スペースで区切ることによって、複数の名前を指定できます。|  
|`crlN.crl`|SPC ファイルに組み込む証明書失効リストの名前。  スペースで区切ることによって、複数の名前を指定できます。|  
|`outputSPCfile.spc`|X.509 証明書が格納される PKCS \#7 オブジェクトの名前。|  
  
|オプション|説明|  
|-----------|--------|  
|**\/?**|このツールのコマンド構文とオプションを表示します。|  
  
## 例  
 `myCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 `oneCertificate.cer` と `twoCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## 参照  
 [ツール](../../../docs/framework/tools/index.md)   
 [Makecert.exe \(証明書作成ツール\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)