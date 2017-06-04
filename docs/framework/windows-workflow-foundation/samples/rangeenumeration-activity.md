---
title: "RangeEnumeration アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# RangeEnumeration アクティビティ
このサンプルでは、数値のコレクションを反復処理するカスタム アクティビティを作成する方法を示します。次の表で、このサンプルに含まれるメイン ファイルについて説明します。  
  
|ファイル名|説明|  
|-----------|--------|  
|RangeEnumeration.cs|<xref:System.Activities.NativeActivity> クラスをオーバーライドし、一連の数値をループする `RangeEnumeration` というカスタム アクティビティを定義します。|  
|RangeEnumerationSample.cs|`RangeEnumeration` アクティビティを使用して数値のコレクションを反復処理するクライアント アプリケーション。|  
  
 次の表で、`RangeEnumeration` アクティビティのプロパティについて説明します。  
  
|プロパティ|説明|  
|-----------|--------|  
|Start|ループの開始位置を示す整数。|  
|Stop|ループの停止位置を示す整数。|  
|Step|各反復処理の反復回数を指定します。|  
|Body|各反復処理中に実行するコードを指定します。|  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、RangeEnumeration.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`  
  
## 参照