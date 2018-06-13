---
title: 既存のサービス コントラクトを使用するワークフロー サービスを作成する方法
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 146b3bba3a880c780644eecd277827823793b5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515306"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>既存のサービス コントラクトを使用するワークフロー サービスを作成する方法
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、コントラクト優先ワークフローの開発という形で、Web サービスとワークフローの統合が向上しています。 コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。 その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。  
  
> [!NOTE]
>  このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。 コントラクト優先ワークフロー サービスの開発の詳細については、次を参照してください。[コントラクト最初のワークフロー サービス開発](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)です。  
  
### <a name="creating-the-workflow-project"></a>ワークフロー プロジェクトの作成  
  
1.  Visual Studio で、次のように選択します。**ファイル**、**新しいプロジェクト**です。 選択、 **WCF**ノードの下、 **c#** 内のノード、**テンプレート**ツリー、および選択、 **WCF ワークフロー サービス アプリケーション**テンプレート。  
  
2.  新しいプロジェクトの名前`ContractFirst` をクリック**Ok**です。  
  
### <a name="creating-the-service-contract"></a>サービス コントラクトの作成  
  
1.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加**. 選択、**コード**、左側のノードと**クラス**右側のテンプレートです。 新しいクラスの名前を`IBookService` をクリック**Ok**です。  
  
2.  表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  サンプルのクラス定義を次のインターフェイス定義に変更します。  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  キーを押してプロジェクトをビルド**Ctrl + Shift + B**です。  
  
### <a name="importing-the-service-contract"></a>サービス コントラクトのインポート  
  
1.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**サービス コントラクトのインポート**です。 **\<現在のプロジェクト >** すべてのサブノードを開き、選択**IBookService**です。 **[OK]** をクリックします。  
  
2.  ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。 **[OK]** をクリックします。  
  
3.  キーを押してプロジェクトをビルド**Ctrl + Shift + B**インポートしたアクティビティがツールボックスに表示されるように、します。  
  
4.  **ソリューション エクスプ ローラー**Service1.xamlx を開きます。 ワークフロー サービスがデザイナーに表示されます。  
  
5.  選択、**シーケンス**アクティビティ。 [プロパティ] ウィンドウ、**しています.** ボタンをクリックして、 **ImplementedContract**プロパティです。 **型コレクション エディター**ウィンドウが表示されたら、をクリックして、**型**ドロップダウン リストを選択し、**型を参照しています.** エントリです。 **型の参照と選択 .Net**ダイアログで、 **\<現在のプロジェクト >** すべてのサブノードを開き、選択**IBookService**です。 **[OK]** をクリックします。 **型コレクション エディター**ダイアログ ボックスで、をクリックして**OK**です。  
  
6.  選択し、削除、 **ReceiveRequest**と**SendResponse**アクティビティ。  
  
7.  ツールボックスからドラッグして、 **Buy_ReceiveAndSendReply**と**Checkout_Receive**上にアクティビティ、**シーケンシャル サービス**アクティビティ。
