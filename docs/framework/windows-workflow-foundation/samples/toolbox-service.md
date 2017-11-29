---
title: "ツールボックス サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 816fb3a8964e5f990c496c73624ebb8c9c1053a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="toolbox-service"></a>ツールボックス サービス
このサンプルでは、ワークフローのコンテキストに基づいて [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ツールボックス アクティビティを更新する方法を示します。 このサンプルには、カスタム アクティビティが選択されているかどうかに基づいてツールボックスの内容を変更するワークフローが含まれています。  
  
## <a name="discussion"></a>説明  
 ワークフローの作成中には、通常、状況に応じてツールボックスが変化することが求められます。 たとえば、特定のアクティビティをワークフローに追加すると、別のアクティビティがいくつかツールボックスに表示されるようにすることが必要な場合があります。 アクティビティをワークフローから削除したときは、ドメインの要件に基づいてツールボックスが適切に応答する必要があります。  
  
 ホストを変更したワークフロー デザイナーでは、ツールボックス コントロールを制御し、ワークフローのモデル変更に基づいて、ホストによってツールボックス コントロールで適切な変更がトリガーされるようにすることができます。 ただし、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] では、ツールボックスをユーザーが制御することはないので、その内容を変更するにはインターフェイスが必要です。 `IActivityToolboxService` がそのインターフェイスに当たります。  
  
 この API には、次の 4 つのメソッドが用意されています。  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WorkflowSimulator.sln ソリューション ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Workflow.xaml ファイルを開きます。  
  
4.  追加、 **[customactivity]**にドラッグして、ツールボックスから削除します。 ツールボックス カテゴリの追加と呼ばれることに注意してください: **New WF Category**の他のアクティビティと**割り当てる**です。  
  
5.  現在の選択を解除、 **[customactivity]**別のアクティビティをドラッグします。  
  
6.  項目**割り当てる**カテゴリで**New WF Category**ツールボックスの下では削除されました。 また、このカテゴリには項目がほかにないので、カテゴリも削除されます。  
  
7.  選択、 **[customactivity]**再度とカテゴリと**割り当てる**アクティビティが再度追加します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
