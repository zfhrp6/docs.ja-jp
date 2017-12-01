---
title: "基本的な XAML 専用サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 004a37682b855135998ef4620e673421f769326d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="basic-xaml-only-service"></a>基本的な XAML 専用サービス
このサンプルでは、XAML 専用サービスを作成する方法を示します。 このシナリオは自動車関連の問題に対する診断サービスです。 このサービスは、顧客に一連の質問をして問題を診断するワークフローとして実装されます。 このサービスで診断できる問題は 2 種類です (車のエンジンがかからない、または空調装置が動作しない)。 ワークフローでは、デザイナーの要求/応答テンプレートを使用して、3 つの簡単なサービス操作を公開します。 サービスは、IIS に仮想ディレクトリを作成し、service1.xamlx ファイルおよび Web.config ファイルをその仮想ディレクトリにコピーすることによって IIS でホストされます。コンパイルされたコードは必要ありません。 既定ではこのサンプルは自動的に必要なファイルにコピー WCF および WF のサンプルのセットアップ手順をたどるときに作成された仮想ディレクトリ: [WindowsCommunicationFoundationサンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010 でのビルド時にします。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  [ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。  
  
3.  オプションが出力されるので、オプションを選択します。 質問が表示されたら、はいかいいえで (Y キーまたは N キーを使用して) 回答します。 サービスによる問題の診断が完了すると、診断結果が出力されます。  
  
4.  オプションが再度表示されます。 もう一度問題を診断することも、アプリケーションを終了することもできます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`