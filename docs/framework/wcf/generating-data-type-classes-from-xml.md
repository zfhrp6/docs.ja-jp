---
title: XML からのデータ型クラスの生成
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 6b38a0aea3101c70b3c3ec0c8feb4ee88018b64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498668"
---
# <a name="generating-data-type-classes-from-xml"></a>XML からのデータ型クラスの生成
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、XML からデータ型クラスを生成するための新しい機能があります。 このトピックでは、自動的に、.NET ブログの RSS フィードのデータ型を生成する方法について説明します。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>フィード .NET ブログの RSS から XML を取得します。  
  
1.  Internet Explorer に移動、 [.NET ブログの RSS フィード](https://blogs.msdn.microsoft.com/dotnet/feed/)です。  
  
2.  ページを右クリックし **ソースの表示**です。  
  
3.  キーを押して、フィードのテキストをコピー **ctrl キーを押しながら A**すべてのテキストを選択して**Ctrl + C**をコピーします。  
  
### <a name="creating-the-data-types"></a>データ型の作成  
  
1.  プロキシが使用されるコード ファイルを開きます。 このファイルは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] プロジェクトの一部である必要があります。  
  
2.  既存のクラスの外部にあるファイルの場所にカーソルを置きます。  
  
3.  選択**編集**、**ペースト**、 **XML をクラスとして貼り付ける**です。  
  
4.  クラスと呼ばれる`link`、 `rss`、 `rssChannel`、 `rssChannelImage`、`rssChannelItem`と`rssChannelItemGuid`RSS フィード内の要素にアクセスするために必要なメンバーで作成されます。  
  
### <a name="using-the-generated-classes"></a>生成されたクラスの使用  
  
1.  クラスが生成されると、他のクラスのコードなどで使用できます。 次のコード例では、`rssChannelImage` クラスの新しいインスタンスが返されます。  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
