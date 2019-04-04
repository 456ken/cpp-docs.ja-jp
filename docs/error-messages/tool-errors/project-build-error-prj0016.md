---
title: プロジェクト ビルド エラー PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: ada89b074fd8e0c2bfc75ba833e9c5966a145312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616867"
---
# <a name="project-build-error-prj0016"></a>プロジェクト ビルド エラー PRJ0016

ユーザーのセキュリティ設定は、プロセスが作成されないようにします。 これらの設定は、構築するために必要です。

プロセスを使用してプロセスを作成するアクセス許可を持っていないユーザーのユーザーとしてログインしています。 このユーザー アカウントのアクセス許可レベルを変更するか、アカウント管理者にお問い合わせください。

このエラーは、次のレジストリ キーが設定されている場合にも発生します。

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

このエラーを解決するには、RestrictRun のキーを削除します。 このレジストリ キーが必要な場合は、追加**vcspawn.exe**キーのエントリの一覧にします。

このエラーのもう 1 つの原因は、ポリシーの設定は含まれていません VCSpawn.exe HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun レジストリ キーの下でこのユーザー アカウントに許可されているウィンドウ プログラムとしてです。

詳細については、[システム ポリシーの設定に準拠する](https://msdn.microsoft.com/library/aa372139)、"許可された Windows アプリケーションだけを実行する"に関するセクションでを参照してください。