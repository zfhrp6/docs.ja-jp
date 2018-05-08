---
title: '方法 : サービス モニカーを登録および構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 1d245327c1e7d53de9a88c93ff0399d8e231a1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>方法 : サービス モニカーを登録および構成する
型付きコントラクトで、Windows Communication Foundation (WCF) サービス モニカーを COM アプリケーションを使用する前を COM に必要な属性型を登録して必要なバインドと、COM アプリケーションとモニカーを構成する必要があります。構成します。  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>必要な属性を備えた型を COM に登録するには  
  
1.  使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを WCF サービスからメタデータのコントラクトを取得します。 これは、WCF クライアント アセンブリおよびクライアント アプリケーション構成ファイルをソース コードを生成します。  
  
2.  アセンブリ内で定義されている型に `ComVisible` という設定をします。 Visual Studio プロジェクトで、AssemblyInfo.cs ファイルに次の属性を追加してください。  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  厳密な名前のアセンブリとマネージの WCF クライアントをコンパイルします。 そのためには暗号キー ペアで署名する必要があります。 詳細については、次を参照してください。[厳密な名前でアセンブリに署名](http://go.microsoft.com/fwlink/?LinkId=94874)、.NET 開発者ガイド 』 でします。  
  
4.  アセンブリ登録 (Regasm.exe) ツールに `/tlb` オプションを指定して、アセンブリで定義されている型を COM に登録します。  
  
5.  グローバル アセンブリ キャッシュ ツール (Gacutil.exe) で、グローバル アセンブリ キャッシュにアセンブリを追加します。  
  
    > [!NOTE]
    >  アセンブリへの署名とグローバル アセンブリ キャッシュへの追加は、必須ではありません。しかしこれを済ませておくと、実行時には、適切な場所からアセンブリを読み込むための手順が簡単になります。  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>COM アプリケーションとモニカーに必要なバインディングを設定するには  
  
-   バインディングの定義を配置 (によって生成された、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成されたクライアント アプリケーション構成ファイルに) クライアント アプリケーションの構成ファイルにします。 たとえば、Visual Basic 6.0 で開発した実行可能ファイルの名前が CallCenterClient.exe の場合、これと同じディレクトリに、CallCenterConfig.exe.config という名前で構成ファイルを作成します。 するとクライアント アプリケーションはモニカーを使えるようになります。 バインド構成は必要ありません、標準バインド WCF に用意された型のいずれかを使用する場合に注意してください。  
  
     次の型が登録されています。  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     このアプリケーションは、`wsHttpBinding` バインディングを使用して公開されています。 このような型とアプリケーション設定であれば、次のようなモニカー文字列が使用されます。  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     `IMathService` 型を定義するアセンブリへの参照を追加すれば、次のコード例のように、Visual Basic 6.0 アプリケーションに上記のモニカー文字列 (どちらの形式でも可) を記述できるようになります。  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     この例で、バインディング構成 `Binding1` の定義は、クライアント アプリケーションごとに、vb6appname.exe.config など該当する名前の構成ファイルに記述します。  
  
    > [!NOTE]
    >  同様のコードを C#、C++、およびその他の .NET 言語アプリケーションで使用できます。  
  
    > [!NOTE]
    >  モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。 このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
     このトピックでは、主に VB 6.0 コードからサービス モニカーを使用する方法について説明していますが、他の言語からサービス モニカーを使用することもできます。 C++ コードからモニカーを使用している場合、次のコードに示すように、Svcutil.exe によって生成されたアセンブリを、"no_namespace named_guids raw_interfaces_only" と共にインポートする必要があります。  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     これにより、インポートされたインターフェイス定義は、すべてのメソッドが `HResult` を返すように変更されます。 他の戻り値は、出力パラメーターに変換されます。 メソッドの実行全体は、同じままです。 このために、プロキシでメソッドを呼び出したときの例外の原因を特定できます。 この機能は C++ コードからのみ使用できます。  
  
## <a name="see-also"></a>関連項目  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
