# <a name="contributing-to-the-project-rome-documentation"></a>プロジェクトのローマ ドキュメントへの投稿

ドキュメントに関心をありがとうございます。 編集、追加、および、ドキュメントを向上させる方法、フィードバックを歓迎いたします。このページは、基本的な手順と貢献するためのガイドラインについて説明します。

## <a name="sign-a-cla"></a>CLA に署名します。

複数のいくつかの行を投稿する Microsoft の従業員がない場合は、する必要があります[Microsoft コントリビューション ライセンス契約 (CLA) に署名する](https://cla.microsoft.com/)します。 

## <a name="propose-a-minor-change"></a>小さな変更を提案します。

ドキュメントを簡単に変更を提案するには、次の手順に従います。

1. Docs.microsoft.com のページを表示する場合にクリックして、**編集**ページの右上隅のボタンをクリックします。  内の対応するマークダウン ソース ファイルにリダイレクトする、 [GitHub リポジトリ](https://github.com/MicrosoftDocs/project-rome)します。 GitHub リポジトリにしている場合だけを変更するにはソース ファイルに移動できます。
2. GitHub アカウントがない場合はクリックして**サインアップ**上にあるし、新しいアカウントを作成します。
3. GitHub ページで変更するには、鉛筆アイコンをクリックします。 
4. ファイルを変更し、[プレビュー] タブを使用して、変更が適切に表示することを確認します。
5. 完了すると、変更をコミットし、プル要求を開きます。

プル要求を作成した後に、Windows 10 の docs チームのメンバーを確認します。 更新プログラムを公開する場合は、要求が受け入れられる[ https://docs.microsoft.com/windows/project-rome/](https://docs.microsoft.com/windows/project-rome/)します。

## <a name="make-more-substantial-changes"></a>大きな変更を加える

### <a name="fork-the-github-repo"></a>GitHub リポジトリをフォークします。

既存の記事に大幅に変更、追加またはイメージを変更または新しい記事を投稿、お勧め、GitHub アカウントにリポジトリをフォーク (の右上隅にある「フォーク」ボタンをクリックして、 [GitHub リポジトリ](https://github.com/MicrosoftDocs/project-rome)、し、ローカル クローンを作成する (緑のをクリックして**複製またはダウンロード**ボタンをコピーしてクリップボードにし、コマンドラインで入力`git clone <paste your repo clone link>`)。

詳細については、次を参照してください。[リポジトリをフォークする](https://help.github.com/articles/fork-a-repo/)します。

Git の使用に慣れていない場合は、次を参照してください。、 [Lynda.com Git Essentials トレーニング](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html)します。

### <a name="author-your-contribution"></a>投稿物を作成します。

フォークし、ローカル コンピューターにリポジトリを複製、好みのテキスト エディターを使って作成を開始できます。 お勧め[Visual Studio Code](https://code.visualstudio.com/)、Microsoft から無料の軽量なオープン ソース エディター。

### <a name="submit-your-contribution-by-issuing-a-pull-request-pr"></a>プル要求 (PR) を発行して内容を送信します。

ローカル git リポジトリに変更を保存した後をコミットし、独自のローカル フォークしたリポジトリにプッシュするコマンド ラインで、次のコマンドを入力します。
- `git status` :このコマンドでは、これらの変更しようとしたことを確認するように変更したファイルの種類を示します。 
- `git add -A` :このコマンドは、インデックスの変更に、すべての変更を追加します。 特定のファイルの変更のみを追加する場合は、コマンドを入力:`git add <yourfile.md>`します。
- `git commit -m "your commit message"` :このコマンドは、行った変更を説明する短いメッセージと共に、前の手順で追加した変更をコミットする git に指示します。
- `git push origin <yourbranchname>` :このコマンドは、指定したブランチに変更を ("origin") の GitHub のフォークをリモート リポジトリにプッシュします。

電子メールが、リモート リポジトリに投稿物をプッシュした後送信される*発行オープンのビルド サービス*投稿物が正常にビルドされたかどうかを通知して、エラーや、リポジトリにある警告へのリンクを提供します。壊れたリンクなど。 サイトで事前設定コンテンツを表示するレポートのリンクをクリックします。 PR を送信する準備が完了したら、変更はエラーと警告のオフの場合、
- プロジェクト ローマ リポジトリのフォークに移動: https://github.com/  **\<your github エイリアス\>**/project-rome します。
- をクリックして、**新しいプル要求**ボタンをクリックします。 "基本フォーク:""MicrosoftDocs/プロジェクト-rome"、として表示されます、および"ヘッド フォーク:"リポジトリとブランチの変更を加えたのフォークを表示する必要があります。 ここで、変更をも確認できます。 
- をクリックして、**プル要求の作成**ボタンをクリックします。 タイトルと説明は、PR を付与する必要があります。 最後にクリックして、**プル要求の作成**もう一度ボタンをクリックします。

PR が送信されると、Windows 10 の docs チームのメンバーを確認します。 要求が受け入れられることができますに変更を確認する、[ステージング サイト](https://review.docs.microsoft.com/windows/project-rome/)します。 これらの更新プログラムが最終的に発行されますライブ[ https://docs.microsoft.com/windows/project-rome/](https://docs.microsoft.com/windows/project-rome/)します。

## <a name="using-issues-to-provide-feedback-on-project-rome-documentation"></a>問題を使用してプロジェクト ローマ ドキュメントに関するフィードバックを提供するには

フィードバックを提供するドキュメントのページを直接変更するのではなく[問題を作成](https://github.com/MicrosoftDocs/project-rome/issues)です。

必ず、トピック タイトルと問題のページの URL が含まれます。

## <a name="additional-resources"></a>その他の資料
- [作成と GitHub の書式設定の概要](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Microsoft の従業員向けの他のリソース
- [GitHub アカウントと MS 別名を接続します。](https://review.docs.microsoft.com/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Markdown を記述するためのリソース](https://review.docs.microsoft.com/windows-authoring-guide/writing-guidance/writing-markdown)