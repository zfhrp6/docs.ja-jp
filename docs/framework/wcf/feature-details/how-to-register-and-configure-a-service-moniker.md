---
title: "方法 : サービス モニカーを登録および構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "COM [WCF], サービス モニカーの構成"
  - "COM [WCF], サービス モニカーの登録"
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# 方法 : サービス モニカーを登録および構成する
COM アプリケーションの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス モニカーを型付きコントラクトで使うには、必要な属性を備えた型を COM に登録し、COM アプリケーションとモニカーに、必要なバインディング設定を組み込まなければなりません。  
  
### 必要な属性を備えた型を COM に登録するには  
  
1.  [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスからメタデータ コントラクトを取得します。  これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリに組み込むソース コードと、クライアント アプリケーションの構成ファイルが生成されます。  
  
2.  アセンブリ内で定義されている型に `ComVisible` という設定をします。  Visual Studio プロジェクトで、AssemblyInfo.cs ファイルに次の属性を追加してください。  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  マネージ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを、厳密な名前のアセンブリとしてコンパイルします。  そのためには暗号キー ペアで署名する必要があります。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 『.NET 開発者ガイド』の「[厳密な名前でのアセンブリへの署名](http://go.microsoft.com/fwlink/?LinkId=94874)」を参照してください。  
  
4.  アセンブリ登録 \(Regasm.exe\) ツールに `/tlb` オプションを指定して、アセンブリで定義されている型を COM に登録します。  
  
5.  グローバル アセンブリ キャッシュ ツール \(Gacutil.exe\) で、グローバル アセンブリ キャッシュにアセンブリを追加します。  
  
    > [!NOTE]
    >  アセンブリへの署名とグローバル アセンブリ キャッシュへの追加は、必須ではありません。しかしこれを済ませておくと、実行時には、適切な場所からアセンブリを読み込むための手順が簡単になります。  
  
### COM アプリケーションとモニカーに必要なバインディングを設定するには  
  
-   [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) で生成したバインディング定義を、クライアント アプリケーションの構成ファイルにコピーします。  たとえば、Visual Basic 6.0 で開発した実行可能ファイルの名前が CallCenterClient.exe の場合、これと同じディレクトリに、CallCenterConfig.exe.config という名前で構成ファイルを作成します。  するとクライアント アプリケーションはモニカーを使えるようになります。  なお、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に組み込まれている標準のバインディング型を使うのであれば、バインディングの設定は必要ありません。  
  
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
  
     このアプリケーションは、`wsHttpBinding` バインディングを使用して公開されています。  このような型とアプリケーション設定であれば、次のようなモニカー文字列が使用されます。  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
  
    ```  
  
     `IMathService` 型を定義するアセンブリへの参照を追加すれば、次のコード例のように、Visual Basic 6.0 アプリケーションに上記のモニカー文字列 \(どちらの形式でも可\) を記述できるようになります。  
  
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
    >  同様のコードを C\#、C\+\+、およびその他の .NET 言語アプリケーションで使用できます。  
  
    > [!NOTE]
    >  モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。  このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
     このトピックでは、主に VB 6.0 コードからサービス モニカーを使用する方法について説明していますが、他の言語からサービス モニカーを使用することもできます。  C\+\+ コードからモニカーを使用している場合、次のコードに示すように、Svcutil.exe によって生成されたアセンブリを、"no\_namespace named\_guids raw\_interfaces\_only" と共にインポートする必要があります。  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     これにより、インポートされたインターフェイス定義は、すべてのメソッドが `HResult` を返すように変更されます。  他の戻り値は、出力パラメーターに変換されます。  メソッドの実行全体は、同じままです。  このために、プロキシでメソッドを呼び出したときの例外の原因を特定できます。  この機能は C\+\+ コードからのみ使用できます。  
  
## 参照  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)