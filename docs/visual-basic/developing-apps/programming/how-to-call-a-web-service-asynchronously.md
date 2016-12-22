---
title: "How to: Call a Web Service Asynchronously (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "asynchronous calls"
  - "Web services, accessing"
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Call a Web Service Asynchronously (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

この例では、Web サービスの非同期ハンドラー イベントにハンドラーをアタッチして、非同期メソッド呼び出しの結果を取得できるようにします。  この例では、DemoTemperatureService Web サービスを使用しています \(http:\/\/www.xmethods.  net\)。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) でプロジェクトの Web サービスを参照すると、この Web サービスが `My.WebServices` オブジェクトに追加され、指定された Web サービスにアクセスするためのクライアント プロキシ クラスが IDE によって生成されます。  
  
 プロキシ クラスを使用すると、Web サービス メソッドを同期的に呼び出すことができ、この場合、アプリケーションは関数が完了するまで待機します。  また、プロキシはメソッドを非同期的に呼び出すために使用できる追加のメンバーを作成します。  Web サービス関数 *NameOfWebServiceFunction* ごとに、プロキシは *NameOfWebServiceFunction*`Async` サブルーチン、*NameOfWebServiceFunction*`Completed` イベント、および *NameOfWebServiceFunction*`CompletedEventArgs` クラスを作成します。  この例では、DemoTemperatureService Web サービスの `getTemp` 関数にアクセスする非同期メンバーの使用方法を示します。  
  
> [!NOTE]
>  ASP.NET では `My.WebServices` オブジェクトがサポートされていないため、このコードは Web アプリケーションでは動作しません。  
  
### Web サービスを非同期的に呼び出すには  
  
1.  DemoTemperatureService Web サービス \(http:\/\/www.xmethods.  net\) を参照します。  アドレスは次のとおりです。  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  `getTempCompleted` イベントのイベント ハンドラーを追加します。  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  `Handles` ステートメントを使用して、イベント ハンドラーを `My.WebServices` オブジェクトのイベントに関連付けることはできません。  
  
3.  イベント ハンドラーが `getTempCompleted` イベントに追加されたかどうかを追跡するためのフィールドを追加します。  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  必要に応じて、イベント ハンドラーを `getTempCompleted` イベントに追加するメソッドを追加し、`getTempAsynch` メソッドを呼び出すメソッドを追加します。  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     `getTemp` Web メソッドを非同期的に呼び出すには、`CallGetTempAsync` メソッドを呼び出します。  Web メソッドが終了すると、その戻り値が `getTempCompletedHandler` イベント ハンドラーに渡されます。  
  
## 参照  
 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)