---
title: "バイトストリーム エンコーダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d0984d3989d6441c363730454ea65b0393c94b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bytestream-encoder"></a>バイトストリーム エンコーダー
このサンプルでは、バイト ストリーム エンコーダーの機能を示す `ByteStreamHttpBinding` である <xref:System.ServiceModel.Channels.Binding> を作成する方法を示します。  
  
## <a name="discussion"></a>説明  
 このサンプルでは、標準のバインディング要素 <xref:System.ServiceModel.Channels.Binding> および <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> を使用して、標準の <xref:System.ServiceModel.Channels.HttpTransportBindingElement> を作成する方法を示します。 このサンプルでは、バイト ストリーム エンコーダーを使用して、画像をアップロードおよびダウンロードする方法を示します。 バイト ストリーム エンコーダーの機能は、HTTP トランスポートのみサポートし、信頼できるメッセージングやセキュリティなどの機能はサポートしません。 唯一サポートされる <xref:System.ServiceModel.Channels.MessageVersion> は <xref:System.ServiceModel.Channels.MessageVersion.None%2A> です。  
  
> [!IMPORTANT]
>  このサンプルを [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] または [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)] で実行している場合は、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] をシステム特権で実行していることを確認してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で ByteStreamHttpBinding.sln ファイルを開きます。  
  
2.  ソリューション エクスプ ローラーでプロジェクトを右クリックして、ByteStreamHttpBindingServer プロジェクトの新しいインスタンスを開始**デバッグ**、し**新しいインスタンスを開始**コンテキスト メニュー。  
  
3.  ソリューション エクスプ ローラーでプロジェクトを右クリックして、ByteStreamHttpBindingClient プロジェクトの新しいインスタンスを開始**デバッグ**、**新しいインスタンスを開始**コンテキスト メニュー。
