---
title: "XML からのデータ型クラスの生成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# XML からのデータ型クラスの生成
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、XML からデータ型クラスを生成するための新しい機能があります。  このトピックでは、MSDN ライブラリの RSS フィードのデータ型を自動的に生成する方法について説明します。  
  
### MSDN ライブラリの RSS フィードからの XML の取得  
  
1.  Internet Explorer で、[MSDN RSS フィード](http://go.microsoft.com/fwlink/?LinkId=225209)に移動します。  
  
2.  ページを右クリックし、**\[ソースの表示\]** を選択します。  
  
3.  Ctrl キーを押しながら A キーを押してフィードのテキストをすべて選択し、Ctrl キーを押しながら C キーを押してコピーします。  
  
### データ型の作成  
  
1.  プロキシが使用されるコード ファイルを開きます。  このファイルは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] プロジェクトの一部である必要があります。  
  
2.  既存のクラスの外部にあるファイルの場所にカーソルを置きます。  
  
3.  **\[編集\]**、**\[形式を選択して貼り付け\]**、**\[XML をクラスとして貼り付ける\]** の順に選択します。  
  
4.  `rss`、`rssChannel`、`rssChannelImage`、および `rssChannelItem` というクラスは、RSS フィードの要素にアクセスするために必要なメンバーを使用して作成されます。  
  
### 生成されたクラスの使用  
  
1.  クラスが生成されると、他のクラスのコードなどで使用できます。  次のコード例では、`rssChannelImage` クラスの新しいインスタンスが返されます。  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
  
    ```