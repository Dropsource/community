# Dropsource Community Hub

Welcome to the Dropsource community! :wave:

<em>This is a test repo.</em>

(welcome text to follow)

## Member Stories

Check out learnings, tips, and observations from Dropsource community members. <a href="https://forum.dropsource.com/u/sue/">Get in touch if you'd like to share yours!</a>

<table id='medium' style='font-size:small'><tr>

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script type="text/javascript">
$(function () {

	var $content = $('#jsonContent');
	var data = {
		rss_url: 'https://medium.com/feed/@dropsource'
	};

	$.get('https://api.rss2json.com/v1/api.json', data, function (response) {
		if (response.status == 'ok') {
			var output = '';
			$.each(response.items, function (k, item) {
				output += '<td class="med-post">';
				output += '<header>';
				
				var tagIndex = item.description.indexOf('<img'); // Find where the img tag starts
				var srcIndex = item.description.substring(tagIndex).indexOf('src=') + tagIndex; // Find where the src attribute starts
				var srcStart = srcIndex + 5; // Find where the actual image URL starts; 5 for the length of 'src="'
				var srcEnd = item.description.substring(srcStart).indexOf('"') + srcStart; // Find where the URL ends
				var src = item.description.substring(srcStart, srcEnd); // Extract just the URL
				output += '<div class="blog-element"><img class="img-responsive" src="' + src + '"></div></header>';
				output += '<div class="blog-content"><strong><a href="'+ item.link + '">' + item.title + '</a></strong>';
				output += '<div class="post-meta"><em>By ' + item.author + '</em></div>';
				var yourString = item.description.replace(/<img[^>]*>/g,"");
				var maxLength = 200 // maximum number of characters to extract
				//trim the string to the maximum length
				var trimmedString = yourString.substr(0, maxLength);
				//re-trim if we are in the middle of a word
				trimmedString = trimmedString.substr(0, Math.min(trimmedString.length, trimmedString.lastIndexOf(" ")))
				output += '<p>' + trimmedString + '...</p>';
				output += '</div></td>';
				return k < 2;
			});
			$('#medium').append(output);
		}
	});
});
</script>

</tr></table>

## Forum

Access community support, connect to other Dropsource developers, and get involved in the conversation on our forum!

<table id='forum-feed' style='font-size:small'>

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script type="text/javascript">
$(function () {

	var $content = $('#jsonContent');
	var data = {
		rss_url: 'https://forum.dropsource.com/posts.rss'
	};

	$.get('https://api.rss2json.com/v1/api.json', data, function (response) {
		if (response.status == 'ok') {
			var output = '';
			$.each(response.items, function (k, item) {
				output += '<tr>';
				var user=item.author.split(' ')[0];
				var avatar='https://forum.dropsource.com/user_avatar/forum.dropsource.com/'+user.substring(1)+'/240/110_1.png';
				output+='<td><img src="'+avatar+'" width="100px" style="border-radius:50px"/></td>';
				output+='<td class="forum-post">';
				output += '<div class="blog-content"><strong><a href="'+ item.link + '">' + item.title + '</a></strong>';
				
				output += '<div class="post-meta"><em>By ' + user + '</em></div>';
				var yourString = item.description.replace(/<img[^>]*>/g,"");
				var maxLength = 200 // maximum number of characters to extract
				//trim the string to the maximum length
				var trimmedString = yourString.substr(0, maxLength);
				//re-trim if we are in the middle of a word
				trimmedString = trimmedString.substr(0, Math.min(trimmedString.length, trimmedString.lastIndexOf(" ")))
				output += '<p>' + trimmedString + '...</p>';
				output += '</div></td></tr>';
				return k < 5;
			});
			$('#forum-feed').append(output);
		}
	});
});
</script>

</table>

## Future

(to follow)

## Resources

(to follow)