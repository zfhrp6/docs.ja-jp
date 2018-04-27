---
title: 'チュートリアル : 拡張性のあるアプリケーションの作成'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: 32
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8946e30ac9d7a224af7801bc721e7d9cf6e1fab0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a>チュートリアル : 拡張性のあるアプリケーションの作成
このチュートリアルでは、簡単な電卓の機能を実行するアドイン用のパイプラインを作成する方法について説明します。 実際のシナリオでは; は示しません代わりに、パイプラインとどのように追加のサービスを提供できるホストの基本機能を示します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   Visual Studio ソリューションを作成します。  
  
-   パイプライン ディレクトリ構造を作成します。  
  
-   コントラクトおよびビューを作成します。  
  
-   アドイン側アダプターを作成します。  
  
-   ホスト側のアダプターを作成します。  
  
-   ホストを作成します。  
  
-   アドインを作成しています。  
  
-   パイプラインを展開します。  
  
-   ホスト アプリケーションを実行します。  
  
 このパイプラインは、シリアル化できる型のみを渡します (<xref:System.Double>と<xref:System.String>)、ホストとアドインの間です。 例については複雑なデータ型のコレクションを渡す方法を示す、次を参照してください。[チュートリアル: コレクションのホスト間で渡すとアドイン](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)です。  
  
 このパイプラインのコントラクトは、次の 4 つの算術演算のオブジェクト モデルを定義します。 追加、減算、乗算、および除算します。 ホストから、アドイン + 2 + 2 などを計算する数式れ、アドインのホストに結果を返します。  
  
 バージョン 2 の電卓を追加より高度を提供し、バージョン管理を示します。 説明されている、[チュートリアル: 変更のホストとしての旧バージョンとの互換性を有効にすると](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Visual Studio  
  
## <a name="creating-a-visual-studio-solution"></a>Visual Studio ソリューションを作成します。  
 Visual Studio でソリューションを使用すると、パイプライン、セグメントのプロジェクトを含むです。  
  
#### <a name="to-create-the-pipeline-solution"></a>パイプライン ソリューションを作成するには  
  
1.  Visual Studio で、という名前の新しいプロジェクトを作成する`Calc1Contract`です。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  ソリューションの名前を付けます`CalculatorV1`です。  
  
## <a name="creating-the-pipeline-directory-structure"></a>パイプライン ディレクトリ構造を作成します。  
 アドイン モデルでは、指定したディレクトリ構造に配置するのにパイプライン セグメントのアセンブリが必要です。 パイプラインの構造に関する詳細については、次を参照してください。[パイプラインの開発要件](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>パイプライン ディレクトリ構造を作成するには  
  
1.  コンピューターの任意の場所、アプリケーションのフォルダーを作成します。  
  
2.  そのフォルダー内には、次のような構造を作成します。  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     アプリケーション フォルダーにパイプラインのフォルダー構造を配置する必要はありません。関数は、のみ、便宜上、ここで呼び出されます。 該当の手順では、このチュートリアルは、パイプラインのフォルダー構造が別の場所である場合は、コードを変更する方法を説明します。 パイプライン ディレクトリの必要条件の説明を参照して[パイプラインの開発要件](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。  
  
    > [!NOTE]
    >  `CalcV2`フォルダーは、このチュートリアルでは使用されません。 のプレース ホルダーは[チュートリアル: 変更のホストとしての旧バージョンとの互換性を有効にすると](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)です。  
  
## <a name="creating-the-contract-and-views"></a>コントラクトとビューの作成  
 このパイプラインのコントラクト セグメントの定義、`ICalc1Contract`を 4 つのメソッドを定義するインターフェイス: `add`、 `subtract`、 `multiply`、および`divide`です。  
  
#### <a name="to-create-the-contract"></a>コントラクトを作成するには  
  
1.  という名前の Visual Studio ソリューションで`CalculatorV1`を開き、`Calc1Contract`プロジェクト。  
  
2.  **ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1Contract`プロジェクト。  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  **ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト。  
  
4.  **ソリューション エクスプ ローラー**、新しい項目をプロジェクトに追加を使用して、**インターフェイス**テンプレート。 **新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalc1Contract`です。  
  
5.  インターフェイス ファイルで名前空間参照を追加<xref:System.AddIn.Contract>と<xref:System.AddIn.Pipeline>です。  
  
6.  このコントラクト セグメントを完了するのにには、次のコードを使用します。 このインターフェイスが必要です、<xref:System.AddIn.Pipeline.AddInContractAttribute>属性。  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  必要に応じて、Visual Studio ソリューションをビルドします。 最後の手順が各手順は、各プロジェクトがあることを確認した後にビルドし、解決されるまでは、ソリューションを実行することはできません。  
  
 追加のビューと、ホスト ビューのためアドインをアドインの最初のバージョンで特に通常、同じコードがある、同時に、ビューを簡単に作成できます。 1 つだけの要素が異なる: 追加のビューが必要です、<xref:System.AddIn.Pipeline.AddInBaseAttribute>属性がアドインのホスト ビューでは、属性は必要ありませんが、します。  
  
#### <a name="to-create-the-add-in-view"></a>追加のビューを作成するには  
  
1.  という名前の新しいプロジェクトを追加`Calc1AddInView`を`CalculatorV1`ソリューションです。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**に System.AddIn.dll への参照を追加、`Calc1AddInView`プロジェクト。  
  
3.  **ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト、およびプロジェクトへの新しい項目の追加を使用して、**インターフェイス**テンプレート。 **新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalculator`です。  
  
4.  インターフェイス ファイルに名前空間参照を追加<xref:System.AddIn.Pipeline>です。  
  
5.  このアドインでは、ビューを完了するのにには、次のコードを使用します。 このインターフェイスが必要です、<xref:System.AddIn.Pipeline.AddInBaseAttribute>属性。  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  必要に応じて、Visual Studio ソリューションをビルドします。  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>アドインのホスト ビューを作成するには  
  
1.  という名前の新しいプロジェクトを追加`Calc1HVA`を`CalculatorV1`ソリューションです。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト、およびプロジェクトへの新しい項目の追加を使用して、**インターフェイス**テンプレート。 **新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalculator`です。  
  
3.  インターフェイス ファイルでは、アドインのホスト ビューを完了するのに、次のコードを使用します。  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  必要に応じて、Visual Studio ソリューションをビルドします。  
  
## <a name="creating-the-add-in-side-adapter"></a>追加側アダプターを作成します。  
 この追加側アダプターは、1 つのビューからコントラクトのアダプターで構成されます。 このパイプライン セグメントは、コントラクトにアドインをビューから型を変換します。  
  
 このパイプラインでは、アドインによって、ホストにサービスを提供方向で、種類からアドインをホストにします。 アドインのホストからの種類がフローありません、ためにがありません側アドインでこのパイプラインのコントラクトのビューへのアダプターを含める。  
  
#### <a name="to-create-the-add-in-side-adapter"></a>アドイン側アダプターを作成するには  
  
1.  という名前の新しいプロジェクトを追加`Calc1AddInSideAdapter`を`CalculatorV1`ソリューションです。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1AddInSideAdapter`プロジェクト。  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  隣接するパイプライン セグメントのプロジェクトへのプロジェクト参照を追加します。  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  各プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。 Visual Basic を使用して、**参照**のタブ**プロジェクトのプロパティ**を設定する**ローカル コピー**に**False** 2 つのプロジェクト参照のです。  
  
5.  プロジェクトの既定のクラスの名前を変更`CalculatorViewToContractAddInSideAdapter`です。  
  
6.  クラス ファイルで名前空間参照を追加<xref:System.AddIn.Pipeline>です。  
  
7.  クラス ファイルで、隣接するセグメントの名前空間参照を追加:`CalcAddInViews`と`CalculatorContracts`です。 (この名前空間の参照は、Visual basic で`Calc1AddInView.CalcAddInViews`と`Calc1Contract.CalculatorContracts`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。  
  
8.  適用、<xref:System.AddIn.Pipeline.AddInAdapterAttribute>属性を`CalculatorViewToContractAddInSideAdapter`クラスに追加側アダプターとして識別します。  
  
9. ように、`CalculatorViewToContractAddInSideAdapter`クラスは継承<xref:System.AddIn.Pipeline.ContractBase>の既定の実装を提供する、<xref:System.AddIn.Contract.IContract>インターフェイス、および、パイプラインのコントラクト インターフェイスを実装して`ICalc1Contract`です。  
  
10. 受け取るパブリック コンス トラクターを追加、`ICalculator`プライベート フィールドでキャッシュ、および基本クラス コンス トラクターを呼び出します。  
  
11. メンバーを実装する`ICalc1Contract`の対応するメンバーを呼び出すだけ、`ICalculator`インスタンスをコンス トラクターに渡され、結果を返します。 これは、ビューを適合させます (`ICalculator`) をコントラクト (`ICalc1Contract`)。  
  
     次のコードには、完了した追加側アダプターが示されています。  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. 必要に応じて、Visual Studio ソリューションをビルドします。  
  
## <a name="creating-the-host-side-adapter"></a>ホスト側のアダプターを作成します。  
 このホスト側のアダプターは、1 つのコントラクトのビューへのアダプターで構成されます。 このセグメントは、アドインのホスト ビューにコントラクトを適合させます。  
  
 このパイプラインのアドインのホストと型フローにサービスをアドインをホストから提供します。 型が、アドインをホストからフローないため、ビューからコントラクトのアダプターが含まするはありません。  
  
 有効期間の管理を実装するには、使用、<xref:System.AddIn.Pipeline.ContractHandle>コントラクトに有効期間トークンをアタッチするオブジェクト。 有効期間の管理が機能するために、このハンドルへの参照を維持する必要があります。 トークンが適用されると、追加のプログラミングは必要ありませんが使用されていないガベージ コレクションで利用できるようにすると、アドイン システムがオブジェクトの破棄できます。 詳細については、次を参照してください。[継続時間管理](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)です。  
  
#### <a name="to-create-the-host-side-adapter"></a>ホスト側のアダプターを作成するには  
  
1.  という名前の新しいプロジェクトを追加`Calc1HostSideAdapter`を`CalculatorV1`ソリューションです。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1HostSideAdapter`プロジェクト。  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  隣接するセグメントのプロジェクトへのプロジェクト参照を追加します。  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  各プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。 Visual Basic を使用して、**参照**のタブ**プロジェクトのプロパティ**を設定する**ローカル コピー**に**False** 2 つのプロジェクト参照のです。  
  
5.  プロジェクトの既定のクラスの名前を変更`CalculatorContractToViewHostSideAdapter`です。  
  
6.  クラス ファイルで名前空間参照を追加<xref:System.AddIn.Pipeline>です。  
  
7.  クラス ファイルで、隣接するセグメントの名前空間参照を追加:`CalcHVAs`と`CalculatorContracts`です。 (この名前空間の参照は、Visual basic で`Calc1HVA.CalcHVAs`と`Calc1Contract.CalculatorContracts`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。  
  
8.  適用、<xref:System.AddIn.Pipeline.HostAdapterAttribute>属性を`CalculatorContractToViewHostSideAdapter`クラス、ホスト側のアダプター セグメントとして識別します。  
  
9. ように、`CalculatorContractToViewHostSideAdapter`クラスは、アドインのホスト ビューを表すインターフェイスを実装して: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic で)。  
  
10. パイプラインのコントラクトの型を受け取るパブリック コンス トラクターを追加`ICalc1Contract`です。 コンス トラクターは、コントラクトへの参照をキャッシュする必要があります。 作成し、新しいキャッシュ<xref:System.AddIn.Pipeline.ContractHandle>アドインの有効期間を管理する、コントラクトです。  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle>有効期間の管理に不可欠です。 参照を保持に失敗した場合、<xref:System.AddIn.Pipeline.ContractHandle>オブジェクト、ガベージ コレクションによって回収がおよび、プログラムで想定されていないときに、パイプラインはシャット ダウンします。 これがなど、診断が困難なエラーにつながる<xref:System.AppDomainUnloadedException>です。 シャット ダウンは、パイプラインの有効期間のステージは通常は、この条件は、エラーを検出するために、有効期間管理コードの方法はありません。  
  
11. メンバーを実装する`ICalculator`の対応するメンバーを呼び出すだけ、`ICalc1Contract`インスタンスをコンス トラクターに渡され、結果を返します。 これは、コントラクトを適合させます (`ICalc1Contract`) ビューに (`ICalculator`)。  
  
     次のコードには、完了のホスト側アダプターが示されています。  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. 必要に応じて、Visual Studio ソリューションをビルドします。  
  
## <a name="creating-the-host"></a>ホストの作成  
 ホスト アプリケーションは、アドインのホスト ビュー アドインと対話します。 アドインでは、検出とアクティブ化によって提供されるメソッドを使用して、<xref:System.AddIn.Hosting.AddInStore>と<xref:System.AddIn.Hosting.AddInToken>クラスを次を行うには。  
  
-   パイプラインとアドインでは、情報のキャッシュを更新します。  
  
-   ホスト ビューの種類のアドインの検索`ICalculator`、指定したパイプラインのルート ディレクトリの下。  
  
-   アドインを使用する指定を求めるボックスをオンにします。  
  
-   選択したアドインの指定したセキュリティの信頼レベルで新しいアプリケーション ドメインで有効にします。  
  
-   カスタムの実行`RunCalculator`メソッドで、アドインのホスト ビューで指定されたアドインのメソッドを呼び出します。  
  
#### <a name="to-create-the-host"></a>ホストを作成するには  
  
1.  という名前の新しいプロジェクトを追加`Calc1Host`を`CalculatorV1`ソリューションです。 基になる、**コンソール アプリケーション**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**、System.AddIn.dll アセンブリへの参照を追加、`Calc1Host`プロジェクト。  
  
3.  プロジェクト参照を追加、`Calc1HVA`プロジェクト。 プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。 Visual Basic を使用して、**参照**のタブ**プロジェクト プロパティ**を設定する**ローカル コピー**に**False**です。  
  
4.  クラス ファイル (Visual Basic でのモジュール) の名前を変更`MathHost1`です。  
  
5.  Visual Basic を使用して、**アプリケーション**のタブ、**プロジェクト プロパティ**を設定する ダイアログ ボックス**スタートアップ オブジェクト**に**Sub Main**です。  
  
6.  クラスまたはモジュールのファイルに名前空間参照を追加<xref:System.AddIn.Hosting>です。  
  
7.  クラスまたはモジュールのファイルで、アドインのホスト ビューの名前空間参照を追加:`CalcHVAs`です。 (Visual Basic の場合は、この名前空間の参照は`Calc1HVA.CalcHVAs`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。  
  
8.  **ソリューション エクスプ ローラー**、ソリューションを選択してから、**プロジェクト**メニューを**プロパティ**です。 **ソリューション プロパティ ページ**ダイアログ ボックスで、設定、**シングル スタートアップ プロジェクト**をこのホスト アプリケーション プロジェクト。  
  
9. クラスまたはモジュールのファイルで使用して、<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>キャッシュを更新するメソッド。 使用して、 <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> 、トークンのコレクションを取得および使用するメソッド、<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>アドインをアクティブ化するメソッド。  
  
     次のコードでは、完全なホスト アプリケーションを示します。  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  このコードでは、パイプラインのフォルダー構造が、アプリケーションのフォルダーにあることを前提としています。 他の場所で配置する場合を設定するコードの行を変更、`addInRoot`変数、変数が、パイプライン ディレクトリ構造へのパスが含まれるようにします。  
  
     コードを使用して、`ChooseCalculator`メソッド トークンを一覧表示して、アドインを選択するユーザー入力を求めます。 `RunCalculator`メソッドは、単純な数式を求めるを使用して式を解析して、`Parser`クラス、および、アドインによって返される結果が表示されます。  
  
10. 必要に応じて、Visual Studio ソリューションをビルドします。  
  
## <a name="creating-the-add-in"></a>アドインを作成します。  
 アドインでは、追加のビューで指定されたメソッドを実装します。 このアドインを実装する、 `Add`、 `Subtract`、 `Multiply`、および`Divide`操作と、ホストに、結果を返します。  
  
#### <a name="to-create-the-add-in"></a>アドインを作成するには  
  
1.  という名前の新しいプロジェクトを追加`AddInCalcV1`を`CalculatorV1`ソリューションです。 基になる、**クラス ライブラリ**テンプレート。  
  
2.  **ソリューション エクスプ ローラー**、System.AddIn.dll アセンブリへの参照をプロジェクトに追加します。  
  
3.  プロジェクト参照を追加、`Calc1AddInView`プロジェクト。 プロジェクト参照を選択し、**プロパティ**設定、**ローカル コピー**に**False**です。 Visual Basic を使用して、**参照**のタブ**プロジェクト プロパティ**を設定する**ローカル コピー**に**False**プロジェクト参照のです。  
  
4.  クラスの名前を変更`AddInCalcV1`です。  
  
5.  クラス ファイルに名前空間参照を追加<xref:System.AddIn>および追加のビュー セグメント: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic で)。  
  
6.  適用、<xref:System.AddIn.AddInAttribute>属性を`AddInCalcV1`クラスに、アドインとしてクラスを識別します。  
  
7.  ように、`AddInCalcV1`クラスは、追加のビューを表すインターフェイスを実装して: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic で)。  
  
8.  メンバーを実装`ICalculator`適切な計算の結果を返すことによってです。  
  
     完了したアドインの次のコードを示しています。  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. 必要に応じて、Visual Studio ソリューションをビルドします。  
  
## <a name="deploying-the-pipeline"></a>パイプラインを展開します。  
 ビルドし、必要なパイプライン ディレクトリ構造にアドイン セグメントを配置する準備が整いました。  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>パイプライン、セグメントの配置  
  
1.  ソリューション内の各プロジェクトを使用して、**ビルド**のタブ**プロジェクト プロパティ**(、**コンパイル**Visual Basic でのタブ) の値を設定する、**出力パス** (、**ビルド出力パス**Visual Basic で)。 アプリケーションのフォルダーの名前を付けた場合`MyApp`、次のフォルダーには、プロジェクトでビルドなど。  
  
    |プロジェクト|パス|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  パイプライン フォルダー構造をアプリケーション フォルダー以外の場所に配置することを決定する場合は、それに応じて、テーブルのパスを変更する必要があります。 パイプライン ディレクトリの必要条件の説明を参照して[パイプラインの開発要件](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。  
  
2.  Visual Studio ソリューションをビルドします。  
  
3.  アセンブリが適切なディレクトリにコピーされたことと、余分なアセンブリのコピーが正しくないフォルダーにインストールされていないことを確認するアプリケーションとパイプラインのディレクトリを確認してください。  
  
    > [!NOTE]
    >  変更しなかった場合**ローカル コピー**に**False**の`Calc1AddInView`プロジェクトの参照、`AddInCalcV1`プロジェクト、ローダー コンテキストの問題により、アドインを配置されているからです。  
  
     パイプラインを展開する方法の詳細については、次を参照してください。[パイプラインの開発要件](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。  
  
## <a name="running-the-host-application"></a>ホスト アプリケーションの実行  
 ホストを実行し、アドインを操作する準備が整いました。  
  
#### <a name="to-run-the-host-application"></a>ホスト アプリケーションを実行するには  
  
1.  コマンド プロンプトで アプリケーション ディレクトリに移動し、ホスト アプリケーションを実行`Calc1Host.exe`です。  
  
2.  ホストは、すべて使用可能なアドインの型を検索し、アドインを選択するように求められます。 入力**1** for のみ使用できるアドインです。  
  
3.  など、電卓の式を入力**2 + 2**です。 数字、および、演算子間のスペースを設定する必要があります。  
  
4.  型**終了**キーを押すと、 **Enter**アプリケーションを閉じるにはキー。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ホスト変更時の旧バージョンとの互換性を有効にします。](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [チュートリアル: アドインとホスト間でのコレクションの受け渡し](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [パイプラインの開発要件](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [コントラクト、ビュー、およびアダプター](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [パイプライン開発](../../../docs/framework/add-ins/pipeline-development.md)
