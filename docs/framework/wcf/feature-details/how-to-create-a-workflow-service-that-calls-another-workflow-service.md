---
title: "方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 方法: 別のワークフロー サービスを呼び出すワークフロー サービスを作成する
ワークフロー サービスでは、別のワークフロー サービスから情報を取得することが必要になる場合があります。このトピックでは、別のワークフロー サービスからワークフロー サービスを呼び出す方法について説明します。このトピックでは、2 つのワークフロー サービスを作成します。入力文字列を反転させるメソッドを持つワークフロー サービスと、その最初のサービスを使用して文字列を反転させた後、入力文字列を大文字に変換するワークフロー サービスです。  
  
### Reverser ワークフロー サービスを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者として実行します。  
  
2.  **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。**\[インストールされたテンプレート\]** ペインの **\[ワークフロー\]** ノードで、**\[WCF ワークフロー サービス アプリケーション\]** を選択します。ソリューションに `NestedServices` という名前を付けて、**\[OK\]** をクリックします。  
  
3.  **\[サーバー\]** の **\[ローカル IIS Web サーバーを使用する\]** が選択されていることを確認します。**\[仮想ディレクトリの作成\]** をクリックします。仮想ディレクトリが正しく作成されたことを示すダイアログ ボックスで **\[OK\]** をクリックします。  
  
4.  ソリューション エクスプローラーで、Service1.xamlx を `StringReverserService.xamlx` という名前に変更します。  
  
5.  新しいプロジェクトの **\[プロジェクトのプロパティ\]** ページで、**\[Web\]** タブをクリックします。**\[開始動作\]** を **\[ページを指定する\]** に設定し、StringReverserService.xamlx を開始するページとして選択します。  
  
6.  デザイナーで StringReverserService.xamlx を開いて、既存の `ReceiveRequest` アクティビティおよび `SendReply` アクティビティを削除し、`ReceiveAndSendReply` アクティビティを既存のシーケンス アクティビティにドラッグします。  
  
    1.  **\[OperationName\]** を \[ReverseString\] に設定します。  
  
    2.  **\[ServiceContractName\]** を \[IReverseString\] に設定します。  
  
    3.  **\[CanCreateInstance\]** チェック ボックスをオンにします。  
  
7.  **\[SequentialService\]** アクティビティを選択し、デザイナーの下部にある **\[変数\]** タブをクリックします。StringToReverse と ReversedStringToReturn という文字列型の 2 つの新しい変数を作成します。  
  
8.  **Receive** アクティビティの **\[定義\]** リンクをクリックします。**\[パラメーター\]** をクリックし、StringToReverse に代入する InputString という文字列型のパラメーターを作成します。  
  
9. **SendReplyToReceive** アクティビティの **\[定義\]** リンクをクリックします。**\[パラメーター\]** をクリックし、ReversedStringToReturn に代入される  ReversedString という文字列型のパラメーターを作成します。  
  
10. サービスのロジックを実装するには、StringLibrary というプロジェクトで新しいクラスを作成します。クラスの定義を次のコードに置き換えます。  
  
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
  
11. 入力で ReverseString メソッドを呼び出すには、ツールボックスから **InvokeMethod** アクティビティを **Receive** アクティビティと **SendReply** アクティビティの間の空白にドラッグします。アクティビティのプロパティを次のように設定します。  
  
    1.  **\[MethodName\]**: ReverseString  
  
    2.  **\[結果\]**: ReversedStringToReturn  
  
    3.  **\[パラメーター\]**: 新しいパラメーターを作成し、**\[方向\]** を \[イン\]、**\[型\]** を \[文字列\]、**\[値\]** を \[StringToReverse\] に設定します。  
  
    4.  **\[TargetType\]**: NestedServices.StringLibrary  
  
12. F5 キーを押して、サービスをテストします。表示される \[WCF テスト クライアント\] で、ReverseString\(\) メソッドをダブルクリックします。\[要求\] ペインで、InputString パラメーターの \[値\] に 「`Sample`」と入力します。**\[起動\]** をクリックします。サービスにより "elpmaS" が返されます。  
  
### UpperCaser ワークフロー サービスを作成するには  
  
1.  NestedServices プロジェクトを右クリックして、**\[追加\]**、**\[新しい項目\]** の順に選択します。**\[ワークフロー\]** ノードで、**\[WCF ワークフロー サービス\]** を選択し、新しいサービスに `UpperCaserService` という名前を付けます。**\[追加\]** をクリックします。これにより、UpperCaserService.xamlx という新しいワークフロー サービスがプロジェクトに追加されます。  
  
2.  デザイナーで UpperCaserService.xamlx を開いて、既存の **ReceiveRequest** アクティビティおよび `SendReply` アクティビティを削除し、`ReceiveAndSendReply` アクティビティを既存のシーケンス アクティビティにドラッグします。  
  
    1.  **\[OperationName\]** を \[UpperCaseString\] に設定します。  
  
    2.  **\[ServiceContractName\]** を \[IUpperCaseString\] に設定します。  
  
    3.  **\[CanCreateInstance\]** チェック ボックスをオンにします。  
  
3.  SequentialService アクティビティを選択し、デザイナーの下部にある **\[変数\]** タブをクリックします。StringToUpper、StringToReverse、StringToReturn という文字列型の 3 つの新しい変数を作成します。  
  
4.  **Receive** アクティビティの **\[定義\]** リンクをクリックします。**\[パラメーター\]** をクリックし、StringToUpper に代入する InputString という文字列型のパラメーターを作成します。  
  
5.  **SendReplyToReceive** アクティビティの **\[定義\]** リンクをクリックします。**\[パラメーター\]** をクリックし、StringToReturn に代入される ModifiedString という文字列型のパラメーターを作成します。  
  
6.  サービスのロジックを実装するには、次のコードを使用して、StringLibrary クラスで新しいメソッドを作成します。  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
  
    ```  
  
7.  入力で UpperCaseString メソッドを呼び出すには、ツールボックスから **InvokeMethod** アクティビティを **Receive** アクティビティと **SendReply** アクティビティの間の空白にドラッグします。アクティビティのプロパティを次のように設定します。  
  
    1.  **\[MethodName\]**: UpperCaseString  
  
    2.  **\[結果\]**: StringToReverse  
  
    3.  **\[パラメーター\]**: 新しいパラメーターを作成し、**\[方向\]** を \[イン\]、**\[型\]** を \[文字列\]、**\[値\]** を \[StringToUpper\] に設定します。  
  
    4.  **\[TargetType\]**: NestedServices.StringLibrary  
  
8.  ここで、修正済みの文字列で最初のサービスを呼び出します。プロジェクトを右クリックし、**\[サービス参照の追加\]** をクリックします。http:\/\/localhost\/NestedServices\/StringReverserService.xamlx でサービス参照をサービスに追加し、プロジェクトをビルドして最初の Web サービスにアクセスするカスタム アクティビティを作成します。  
  
9. 新しいアクティビティのインスタンスを、**InvokeMethod** アクティビティと **SendReplyToReceive** アクティビティの間のワークフローにドラッグします。変数 StringToReverse を新しいアクティビティの InputString プロパティに、変数 StringToReturn を StringToReturn プロパティに割り当てます。  
  
10. NestedServices プロジェクトの \[プロパティ\] ページを開き、**\[Web\]** タブの **\[ページを指定する\]** を UpperCaserService.xamlx に変更します。  
  
11. F5 キーを押して、サービスをテストします。表示される \[WCF テスト クライアント\] で、ReverseString\(\) メソッドをダブルクリックします。\[要求\] ペインで、InputString パラメーターの \[値\] に 「`Sample`」と入力します。**\[起動\]** をクリックします。サービスにより "ELPMAS" が返されます。  
  
### サービスを呼び出すクライアントを作成するには  
  
1.  クライアントという新しいコンソール アプリケーション プロジェクトをソリューションに追加します。  
  
2.  クライアント プロジェクトを右クリックして、**\[サービス参照の追加\]** をクリックします。表示されるウィンドウで、**\[探索\]** をクリックします。StringReverserService.xamlx を選択し、名前空間として「ReverseService」と入力します。**\[OK\]** をクリックします。  
  
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