# Reverse-back-MD5-crack-password-in-PHP
<!DOCTYPE html>
<head><title>Nkurunziza Benjamin MD5 Cracker</title></head>
<body>
<h1>MD5 cracker</h1>
<p>This application takes an MD5 hash of a four digit pin and check all 10,000 possible four digit PINs to determine the PIN.</p>
<pre>
Debug Output:
<?php
$goodtext = "Not found";
if ( isset($_GET['md5']) ) {
    $time_pre = microtime(true);
    $md5 = $_GET['md5'];
    $txt = "0123456789";
    $show = 15;
    for($i=0; $i<strlen($txt); $i++ ) {
        $num1 = $txt[$i];  
        for($j=0; $j<strlen($txt); $j++ ) {
            $num2 = $txt[$j]; 
            for($k=0; $k<strlen($txt); $k++ ) {
                $num3 = $txt[$k];  
                for($l=0; $l<strlen($txt); $l++ ) {
                    $num4 = $txt[$l]; 
                    $try = $num1.$num2.$num3.$num4;
                    $check = hash('md5', $try);
                    if ( $check == $md5 ) {
                        $goodtext = $try;
                        break;   
                    }
                    if ( $show > 0 ) {
                        print "$check $try\n";
                        $show = $show - 1;
                }
            }
            }
        }
    }
    $time_post = microtime(true);
    print "Elapsed time: ";
    print $time_post-$time_pre;
    print "\n";
}
 ?>
</pre>
<p>PIN: <?= htmlentities($goodtext); ?></p>
<form>
<input type="text" name="md5" size="40" />
<input type="submit" value="Crack MD5"/>
</form>
<p><a href="index.php">Reset</a></p>
</body>
</html>
