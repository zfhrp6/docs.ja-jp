---
title: 基本的な XAML 専用サービス
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517200"
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`