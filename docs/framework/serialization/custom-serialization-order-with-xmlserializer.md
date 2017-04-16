---
title: "XmlSerializer によるカスタム シリアル化順序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# XmlSerializer によるカスタム シリアル化順序
[サンプルのダウンロード](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 このサンプルでは、XML シリアル化で、シリアル化される要素および逆シリアル化される要素の順序を制御する方法を示します。  
  
 シリアル化の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。  
  
### コマンド プロンプトを使用してサンプルをビルドするには  
  
1.  コマンド プロンプト ウィンドウを開き、サンプルの使用言語に対応するサブディレクトリに移動します。  
  
2.  コマンド ラインで「**msbuild CustomOrder.sln**」と入力します。  
  
### Visual Studio を使用してサンプルをビルドするには  
  
1.  [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。  
  
2.  CustomOrder.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。  
  
3.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
4.  サンプル アプリケーションは、既定の \\bin ディレクトリまたは \\bin\\Debug ディレクトリにビルドされます。  
  
## 参照  
 [System.Runtime.Serialization 名前空間](frlrfSystemRuntimeSerialization)   
 [System.Xml.Serialization 名前空間](frlrfSystemXmlSerialization)   
 [基本的なシリアル化](../../../docs/framework/serialization/basic-serialization.md)   
 [バイナリ シリアル化](../../../docs/framework/serialization/binary-serialization.md)   
 [属性を使用した XML シリアル化の制御](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [XML シリアル化の概要](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [シリアル化](../../../docs/framework/serialization/index.md)   
 [SOAP Service](http://msdn.microsoft.com/ja-jp/2051c992-28d1-499e-961f-17e9b675cec9)   
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)