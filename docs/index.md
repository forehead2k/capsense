
# CapSense Versions

Rough prototype of making CapSense documentation available for all vesions. This happens to be generated from Markdown, but we can do custom HTML here, too.


| Version | Source | Documenation | Notes |
| :-----: | :----: | :----------: | :---: |
| 2.10.0   | [GitHub](https://github.com/cypresssemiconductorco/capsense/tree/release-v2.10.0) | [HTML](https://forehead2k.github.io/capsense/v2.10/docs/capsense_api_reference_manual/html/index.html) | n/a |
| 2.0.0   | [GitHub](https://github.com/cypresssemiconductorco/capsense/tree/release-v2.0.0) | [HTML](https://forehead2k.github.io/capsense/v2.0/docs/capsense_api_reference_manual/html/index.html) | n/a |

# Other Links
[Main Git Repository](https://github.com/cypresssemiconductorco/capsense/)

<script>
const GH_API_URL = 'https://api.github.com/repos/forehead2k/capsense/issues/1/comments';

let request = new XMLHttpRequest();
request.open( 'GET', GH_API_URL, true );
request.onload = function() {
	if ( this.status >= 200 && this.status < 400 ) {
		let response = JSON.parse( this.response );

		for ( var i = 0; i < response.length; i++ ) {
			document.getElementById( 'gh-comments-list' ).appendChild( createCommentEl( response[ i ] ) );
		}

		if ( 0 === response.length ) {
			document.getElementById( 'no-comments-found' ).style.display = 'block';
		}
	} else {
		console.error( this );
	}
};

function createCommentEl( response ) {
	let user = document.createElement( 'a' );
	user.setAttribute( 'href', response.user.url.replace( 'api.github.com/users', 'github.com' ) );
	user.classList.add( 'user' );

	let userAvatar = document.createElement( 'img' );
	userAvatar.classList.add( 'avatar' );
	userAvatar.setAttribute( 'src', response.user.avatar_url );

	user.appendChild( userAvatar );

	let commentLink = document.createElement( 'a' );
	commentLink.setAttribute( 'href', response.html_url );
	commentLink.classList.add( 'comment-url' );
	commentLink.innerHTML = '#' + response.id + ' - ' + response.created_at;

	let commentContents = document.createElement( 'div' );
	commentContents.classList.add( 'comment-content' );
	commentContents.innerHTML = response.body;

	let comment = document.createElement( 'li' );
	comment.setAttribute( 'data-created', response.created_at );
	comment.setAttribute( 'data-author-avatar', response.user.avatar_url );
	comment.setAttribute( 'data-user-url', response.user.url );

	comment.appendChild( user );
	comment.appendChild( commentContents );
	comment.appendChild( commentLink );

	return comment;
}
request.send();
</script>

<hr>

<div class="github-comments">
	<h2>Comments</h2>
	<ul id="gh-comments-list"></ul>
	<p id="leave-a-comment">Join the discussion for this article on <a href="https://github.com/forehead2k/capsense/issues/1">this ticket</a>. Comments appear on this page instantly.</p>
</div>

