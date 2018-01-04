---
title: "方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c99748e77f1fccd9512c8915d0f4068d0da51a41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する
ワークフロー サービスでは、別のワークフロー サービスから情報を取得することが必要になる場合があります。  このトピックでは、別のワークフロー サービスからワークフロー サービスを呼び出す方法について説明します。 このトピックでは、2 つのワークフロー サービスを作成します。入力文字列を反転させるメソッドを持つワークフロー サービスと、その最初のサービスを使用して文字列を反転させた後、入力文字列を大文字に変換するワークフロー サービスです。  
  
### <a name="to-create-the-reverser-workflow-service"></a>Reverser ワークフロー サービスを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者として実行します。  
  
2.  選択**ファイル**、**新しいプロジェクト**です。 下にある、**ワークフロー**内のノード、**インストールされたテンプレート**ペインで、 **WCF ワークフロー サービス アプリケーション**です。 ソリューションの名前を付けます`NestedServices` をクリックし、 **ok**です。  
  
3.  **サーバー**、ことを確認して**ローカル IIS Web サーバー**が選択されています。 をクリックして**仮想ディレクトリを作成**です。 をクリックして**OK**仮想ディレクトリが正常に作成されたことを示すダイアログ ボックスでします。  
  
4.  ソリューション エクスプ ローラーで、名前を変更する Service1.xamlx`StringReverserService.xamlx`です。  
  
5.  **プロジェクト プロパティ**、新しいプロジェクトのページで、をクリックして、 **Web**タブです。設定、**開始動作**に**特定のページ**StringReverserService.xamlx を開始するページとしてを選択します。  
  
6.  デザイナーで StringReverserService.xamlx を開いて、既存の `ReceiveRequest` アクティビティおよび `SendReply` アクティビティを削除し、`ReceiveAndSendReply` アクティビティを既存のシーケンス アクティビティにドラッグします。  
  
    1.  設定、 **OperationName** ReverseString にします。  
  
    2.  設定、 **ServiceContractName** [ireversestring] にします。  
  
    3.  選択、 **CanCreateInstance**チェック ボックスをオンします。  
  
7.  選択、 **SequentialService**クリックして、アクティビティ、**変数**デザイナーの下部にあるタブ。 StringToReverse と ReversedStringToReturn という文字列型の 2 つの新しい変数を作成します。  
  
8.  クリックして、**定義**内のリンク、**受信**アクティビティ。 クリックして、**パラメーター**、型 String StringToReverse に代入する InputString というパラメーターを作成します。  
  
9. クリックして、**定義**内のリンク、 **SendReplyToReceive**アクティビティ。 クリックして、**パラメーター**文字列の型、ReversedStringToReturn に代入される ReversedString というパラメーターを作成します。  
  
10. サービスのロジックを実装するには、StringLibrary というプロジェクトで新しいクラスを作成します。  クラスの定義を次のコードに置き換えます。  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. 入力で ReverseString メソッドを呼び出すには、ドラッグ、 **InvokeMethod**間の空白にアクティビティをツールボックス、**受信**と**SendReply**アクティビティ。 アクティビティのプロパティを次のように設定します。  
  
    1.  **MethodName**: ReverseString  
  
    2.  **結果**: ReversedStringToReturn  
  
    3.  **パラメーター**: 新しいパラメーターを作成、**方向**で、**型**文字列の**値**StringToReverse のです。  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
12. F5 キーを押して、サービスをテストします。 表示される [WCF テスト クライアント] で、ReverseString() メソッドをダブルクリックします。 要求ペインで、次のように入力します。 `Sample` 、InputString パラメーターの値。 をクリックして**呼び出す**です。 サービスにより "elpmaS" が返されます。  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>UpperCaser ワークフロー サービスを作成するには  
  
1.  NestedServices プロジェクトを右クリックし **追加**、**新しい項目の**します。 **ワークフロー**ノード、 **WCF ワークフロー サービス**、新しいサービスの名前と`UpperCaserService`です。 **[追加]**をクリックします。 これにより、UpperCaserService.xamlx という新しいワークフロー サービスがプロジェクトに追加されます。  
  
2.  デザイナーで UpperCaserService.xamlx を開いて、既存の削除**ReceiveRequest**と`SendReply`アクティビティ、およびドラッグ、`ReceiveAndSendReply`アクティビティを既存のシーケンス アクティビティにします。  
  
    1.  設定、 **OperationName** UpperCaseString にします。  
  
    2.  設定、 **ServiceContractName** [iuppercasestring] にします。  
  
    3.  選択、 **CanCreateInstance**チェック ボックスをオンします。  
  
3.  SequentialService アクティビティを選択し、クリックして、**変数**デザイナーの下部にあるタブ。 StringToUpper、StringToReverse、StringToReturn という文字列型の 3 つの新しい変数を作成します。  
  
4.  クリックして、**定義**内のリンク、**受信**アクティビティ。 クリックして、**パラメーター**、型 String StringToUpper に代入する InputString というパラメーターを作成します。  
  
5.  クリックして、**定義**内のリンク、 **SendReplyToReceive**アクティビティ。 クリックして、**パラメーター**文字列型の StringToReturn に代入される ModifiedString というパラメーターを作成します。  
  
6.  サービスのロジックを実装するには、次のコードを使用して、StringLibrary クラスで新しいメソッドを作成します。  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  入力で UpperCaseString メソッドを呼び出すには、ドラッグ、 **InvokeMethod**間の空白にアクティビティをツールボックス、**受信**と**SendReply**アクティビティ。 アクティビティのプロパティを次のように設定します。  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **結果**: StringToReverse  
  
    3.  **パラメーター**: 新しいパラメーターを作成、**方向**で、**型**文字列の**値**StringToUpper のです。  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
8.  ここで、修正済みの文字列で最初のサービスを呼び出します。 プロジェクトを右クリックし **サービス参照の追加**です。 http://localhost/NestedServices/StringReverserService.xamlx でサービス参照をサービスに追加し、プロジェクトをビルドして最初の Web サービスにアクセスするカスタム アクティビティを作成します。  
  
9. 新しいアクティビティのインスタンス、ワークフローにドラッグ間、 **InvokeMethod**アクティビティおよび**SendReplyToReceive**アクティビティ。 変数 StringToReverse を新しいアクティビティの InputString プロパティに、変数 StringToReturn を StringToReturn プロパティに割り当てます。  
  
10. NestedServices プロジェクトのプロパティ ページを開き、変更、**特定ページ**で、 **Web**を UpperCaserService.xamlx にタブです。  
  
11. F5 キーを押して、サービスをテストします。 表示される [WCF テスト クライアント] で、ReverseString() メソッドをダブルクリックします。 要求ペインで、次のように入力します。 `Sample` 、InputString パラメーターの値。 をクリックして**呼び出す**です。 サービスにより "ELPMAS" が返されます。  
  
### <a name="to-create-a-client-to-call-the-services"></a>サービスを呼び出すクライアントを作成するには  
  
1.  クライアントという新しいコンソール アプリケーション プロジェクトをソリューションに追加します。  
  
2.  クライアント プロジェクトを右クリックし **サービス参照の追加**です。 表示されるウィンドウで  **Discover**です。 StringReverserService.xamlx を選択し、名前空間として「ReverseService」と入力します。  **[OK]**をクリックします。  
  
3.  Program.cs の Main メソッドを次のコードで置き換えます。  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
