---
title: ポリシーを使用した注文処理
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: 15e274a7a513a3208e3a54575dc354310743b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519419"
---
# <a name="order-processing-with-policy"></a>ポリシーを使用した注文処理
注文処理ポリシー サンプルでは、Windows WF (Workflow Foundation) の [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] に導入された重要な機能の一部を示しています。 次の機能が WF ルール エンジンに新しく追加されました。  
  
-   演算子のオーバーロードのサポート。  
  
-   `new` 演算子のサポート。これにより、WF ルールから新しいオブジェクトおよび配列を作成できます。  
  
-   拡張メソッドのサポート。これにより、C# のコーディング スタイルとの互換性を持つ拡張メソッドのWF ルールからの呼び出しが容易かつ便利になります。  
  
> [!NOTE]
>  このサンプルでは、ビルドおよび実行のために [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] がインストールされていることが必要です。 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ではプロジェクトとソリューション ファイルを開く必要があります。  
  
 このサンプルでは、使用できるアイテムの番号付きリストと郵便番号で構成される顧客の注文を入力する、`OrderProcessingPolicy` プロジェクトを示します。 両方の入力が正しい場合は、注文が正常に処理されますが、正しくない場合は、ポリシーによってエラー オブジェクトが作成され、オーバーロードされた `+` 演算子と定義済みの拡張メソッドによって、ユーザーにエラーが通知されます。  
  
> [!NOTE]
>  拡張メソッドの詳細については、次を参照してください。 [c# バージョン 3.0 の仕様](http://go.microsoft.com/fwlink/?LinkId=95402)です。  
  
 サンプルは、以下のプロジェクトで構成されます。  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` は、`OrderError` クラスおよび `OrderErrorCollection` クラスを定義するクラス ライブラリです。 `OrderError` インスタンスは、無効な入力が行われたときに作成されます。 ライブラリには、`OrderErrorCollection` 内のすべての `ErrorText` オブジェクトの `OrderError` プロパティを出力する `OrderErrorCollection` クラスの拡張メソッドも用意されています。  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` プロジェクトは、1 つの `PolicyFromFile` アクティビティを定義する WF コンソール アプリケーションです。 このアクティビティには、以下のルールがあります。  
  
    -   `invalidItemNum`  
  
         このルールでは、アイテム番号が 1 ～ 6 の範囲内かどうかが検証されます。 アイテム番号が有効範囲内の場合は、コンソールへの出力を除き、処理は何も行われません。 アイテム番号が 1 ～ 6 の範囲外の場合は、`invalidItemNum` ルールによって以下の処理が行われます。  
  
        1.  新しい `OrderError` オブジェクトを作成し、入力されたアイテム番号をこのオブジェクトに渡して、このオブジェクトの `ErrorText` プロパティおよび `CustomerName` プロパティを設定します。  
  
        2.  `invalidItemNumErrorCollection` オブジェクトを作成します。  
  
        3.  新しく作成した `OrderError` インスタンスを `invalidItemNumErrorCollection` に追加します。  
  
         これは、ルール内でオブジェクトのインスタンスを作成できる `new` 演算子がサポートされていることを示します。  
  
    -   `invalidZip`  
  
         このルールでは、郵便番号が 5 桁で、600 ～ 99998 の範囲内にあるかどうかを検証します。 郵便番号が有効範囲内の場合は、コンソールへの出力を除き、処理は何も行われません。 郵便番号が 5 桁よりも少ないか、郵便番号が 00600 ～ 99998 の範囲外の場合は、`invalidZip` ルールによって以下の処理が行われます。  
  
        1.  `OrderError` オブジェクトを作成し、入力された郵便番号をこのオブジェクトに渡して、このオブジェクトの `ErrorText` プロパティおよび `CustomerName` プロパティを設定します。  
  
        2.  `invalidZipCodeErrorCollection` オブジェクトを作成します。  
  
        3.  新しく作成した `OrderError` インスタンスを、新しく作成した `invalidZipCodeErrorCollection` に追加します。  
  
         このルールで、`new` 演算子のサポートが再度実現され、ルール内でのオブジェクトのインスタンスの作成が可能となります。  
  
    -   `displayErrors`  
  
         このルールでは、上記の 2 つの `OrderErrorCollection` オブジェクト、`invalidItemNumErrorCollection` および `invalidIZipCodeErrorCollection` の 2 つのルールによって追加されたエラーがあるかどうかを確認します。 エラーがある場合 (`invalidItemNumErrorCollection` または `invalidZipCodeErrorCollection`が `null` ではない場合)、このルールによって以下の処理が行われます。  
  
        1.  呼び出し、オーバー ロードされた`+`の内容をコピーする演算子`invalidItemNumErrorCollection`と`invalidZipCodeErrorCollection`を`invalidOrdersCollection``OrderErrorCollection`インスタンス。  
  
        2.  `PrintOrderErrors` の `invalidOrdersCollection` 拡張メソッドを呼び出し、`ErrorText` 内のすべての `orderError` オブジェクトの `invalidOrdersCollection` プロパティを出力します。  
  
 `+` のオーバーロードされた `OrderErrorCollection` 演算子は、`OrderErrorCollection` プロジェクトの `OrderErrorLibrary` クラスで定義されています。 この演算子は、2 つの `OrderErrorCollection` オブジェクトを受け取り、1 つの `OrderErrorCollection` オブジェクトに結合します。  
  
 `PrintOrderErrors` 拡張メソッドも `OrderErrorLibrary` プロジェクトで定義されています。 拡張メソッドは C# の新機能であり、開発者は、クラスの派生や元の型の再コンパイルを行わなくても、新しいメソッドを既存の CLR 型のパブリック コントラクトに追加できます。  
  
 サンプルを実行すると、名前、購入するアイテムの番号、および郵便番号の入力が求められます。 その後、この情報は、ポリシー アクティビティで定義されているルールによって検証されます。 このプログラムの出力サンプルを次に示します。  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で OrderProcessingPolicy.sln プロジェクト ファイルを開きます。  
  
2.  このソリューションには、`OrderErrorLibrary` および `OrderProcessingPolicy` という 2 つの異なるプロジェクトが含まれています。 `OrderProcessingPolicy` プロジェクトでは、`OrderErrorLibrary` プロジェクトで定義されているクラスとメソッドが使用されます。  
  
3.  すべてのプロジェクトをビルドします。  
  
4.  **[実行]** をクリックします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`