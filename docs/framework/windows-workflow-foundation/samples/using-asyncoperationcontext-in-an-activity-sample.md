---
title: アクティビティ サンプルでの AsyncOperationContext の使用
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515498"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>アクティビティ サンプルでの AsyncOperationContext の使用
このサンプルでは、<xref:System.Activities.CodeActivity> を使用してワークフロー外で非同期に作業を実行するカスタムの <xref:System.Activities.AsyncCodeActivityContext> を開発する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 サンプルのアクティビティでは、<xref:System.IO.FileStream.BeginWrite%2A> クラスの <xref:System.IO.FileStream.EndWrite%2A> メソッドおよび <xref:System.IO.FileStream> メソッドを使用して、非同期にデータをファイルに書き込みます。 ここで示すパターンは、他の非同期メソッドでの使用に合わせて変更できます。 非同期操作の実行中、ワークフローの他のアクティビティを実行できますが、ワークフローを永続化することはできません。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Async.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`