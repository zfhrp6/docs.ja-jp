---
title: "ASP.NET 互換性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751fe96caa2be63e925b3107fa2c198b523bef72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-compatibility"></a>ASP.NET 互換性
このサンプルでは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 互換性モードを有効にする方法を示します。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換性モードで実行されるサービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション パイプラインに完全に組み込まれるので、ファイルや URL の承認、セッション状態、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] クラスなどの <xref:System.Web.HttpContext> の機能を使用できるようになります。 <xref:System.Web.HttpContext> クラスを使用すると、クッキー、セッション、およびその他の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 機能にアクセスできます。 このモードでは、バインディングは HTTP トランスポートを使用し、サービス自体は IIS でホストされる必要があります。  
  
 このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!NOTE]
>  このサンプルを実行するには、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] アプリケーション プールが必要です。 新しいアプリケーション プールの作成または既定のアプリケーション プールの変更を行うには、次の手順に従います。  
>   
>  1.  **[コントロール パネル]**を開きます。  開く、**管理ツール**アプレット、**システムとセキュリティ**見出し。 開く、**インターネット インフォメーション サービス (IIS) マネージャー**アプレットします。  
> 2.  ツリー ビューを展開し、**接続**ウィンドウです。 選択、**アプリケーション プール**ノード。  
> 3.  使用する既定のアプリケーション プールを設定する[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)](既存のサイトと非互換性の問題が発生する可能性があります、) を右クリックし、 **DefaultAppPool**リスト項目と選択**基本設定しています.**. 設定、 **.Net Framework のバージョン**プルダウンを**.Net Framework v4.0.30128** (またはそれ以降)。  
> 4.  使用する新しいアプリケーション プールを作成する[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)](互換性を保持する他のアプリケーション)、右クリックし、**アプリケーション プール**ノード**アプリケーション プールの追加しています.**. 新しいアプリケーション プールの名前を指定し、設定、 **.Net Framework のバージョン**プルダウンを**.Net Framework v4.0.30128** (またはそれ以降)。 下、セットアップを実行する手順は、後に右クリックし、 **ServiceModelSamples**アプリケーションと選択**アプリケーションの管理**、**詳細設定しています.**. 設定、**アプリケーション プール**新しいアプリケーション プールにします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)、電卓サービスを実装します。 `ICalculator` コントラクトは、一連の算術演算を実行して実行結果を保持できるように `ICalculatorSession` コントラクトに変更されました。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 サービスはこの機能を使用して、複数のサービス操作が呼び出されて計算を実行する際に、各クライアントの状態を保持します。 クライアントは `Result` を呼び出して現在の結果を取得したり、`Clear` を呼び出してその結果をクリアし、0 にすることができます。  
  
 このサービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッションを使用して、各クライアント セッションの結果を保持します。 これにより、サービスは、サービスへの複数の呼び出しによる各クライアントの実行結果を保持できます。  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッション状態と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションとでは、大きく異なります。  参照してください、[セッション](../../../../docs/framework/wcf/samples/session.md)について[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]セッションです。  
  
 サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッション状態と密接な依存関係にあるので、正常に機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換性モードが必要です。 これらの要件は、`AspNetCompatibilityRequirements` 属性を適用することにより宣言によって表されます。  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行することを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  ソリューションがビルドされたら、Setup.bat を実行し、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で ServiceModelSamples アプリケーションを設定します。 ServiceModelSamples ディレクトリは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションとして表示されます。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
## <a name="see-also"></a>参照  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
