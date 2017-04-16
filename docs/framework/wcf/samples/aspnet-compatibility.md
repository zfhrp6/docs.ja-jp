---
title: "ASP.NET 互換性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# ASP.NET 互換性
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換性モードを有効にする方法を示します。  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換性モードで実行されるサービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション パイプラインに完全に組み込まれるので、ファイルや URL の承認、セッション状態、<xref:System.Web.HttpContext> クラスなどの [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の機能を使用できるようになります。  <xref:System.Web.HttpContext> クラスを使用すると、クッキー、セッション、およびその他の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 機能にアクセスできます。  このモードでは、バインディングは HTTP トランスポートを使用し、サービス自体は IIS でホストされる必要があります。  
  
 このサンプルでは、クライアントはコンソール アプリケーション \(.exe\) で、サービスはインターネット インフォメーション サービス \(IIS\) によってホストされています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!NOTE]
>  このサンプルを実行するには、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] アプリケーション プールが必要です。  新しいアプリケーション プールの作成または既定のアプリケーション プールの変更を行うには、次の手順に従います。  
>   
>  1.  **コントロール パネル**を開きます。  **\[システムとセキュリティ\]** 見出しの下にある **\[管理ツール\]** アプレットを開きます。  **\[インターネット インフォメーション サービス \(IIS\) マネージャー\]** アプレットを開きます。  
> 2.  **\[接続\]** ペインのツリー ビューを展開します。  **\[アプリケーション プール\]** ノードをクリックします。  
> 3.  既定のアプリケーション プールで [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] を使用するように設定する \(既存のサイトとの非互換性の問題が発生する可能性があります\) には、**DefaultAppPool** リスト項目を右クリックして **\[基本設定\]** をクリックします。  **\[.Net Framework バージョン\]** プルダウンを **\[.Net Framework v4.0.30128\]** \(またはそれ以降\) に設定します。  
> 4.  [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] を使用する新しいアプリケーション プールを作成する \(他のアプリケーションの互換性を保持する\) には、**\[アプリケーション プール\]** ノードを右クリックして **\[アプリケーション プールの追加\]** をクリックします。  新しいアプリケーション プールに名前を付けて、**\[.Net Framework バージョン\]** プルダウンを **\[.Net Framework v4.0.30128\]** \(またはそれ以降\) に設定します。  以下のセットアップ手順を実行した後で、**ServiceModelSamples** アプリケーションを右クリックし、**\[アプリケーションの管理\]**、**\[詳細設定…\]** の順にクリックします。  **\[アプリケーション プール\]** を新しいアプリケーション プールに設定します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 このサンプルは、電卓サービスを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  `ICalculator` コントラクトは、一連の算術演算を実行して実行結果を保持できるように `ICalculatorSession` コントラクトに変更されました。  
  
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
  
 サービスはこの機能を使用して、複数のサービス操作が呼び出されて計算を実行する際に、各クライアントの状態を保持します。  クライアントは `Result` を呼び出して現在の結果を取得したり、`Clear` を呼び出してその結果をクリアし、0 にすることができます。  
  
 このサービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッションを使用して、各クライアント セッションの結果を保持します。  これにより、サービスは、サービスへの複数の呼び出しによる各クライアントの実行結果を保持できます。  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッション状態と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションとでは、大きく異なります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションの詳細については、「[セッション](../../../../docs/framework/wcf/samples/session.md)」を参照してください。  
  
 サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッション状態と密接な依存関係にあるので、正常に機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換性モードが必要です。  これらの要件は、`AspNetCompatibilityRequirements` 属性を適用することにより宣言によって表されます。  
  
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
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。  クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
  
```  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  ソリューションがビルドされたら、Setup.bat を実行し、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で ServiceModelSamples アプリケーションを設定します。  ServiceModelSamples ディレクトリは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションとして表示されます。  
  
4.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)