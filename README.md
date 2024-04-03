# Music-Player
# res/Layout

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="@drawable/icon4">


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="30dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/tv_title"
            android:text="Now Playing"
            android:textSize="18sp"
            android:textColor="@color/purple_500"
            android:textStyle="bold"
            android:layout_marginTop="20dp"
            android:fontFamily="sans-serif-condensed-medium"/>


        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/tv_songname"
            android:text="The Kid Laroi,Justin Bieber-Stay"
            android:textSize="14sp"
            android:textColor="@color/black"
            android:textStyle="bold"
            android:layout_marginTop="20dp"
            android:layout_marginLeft="10dp"
            android:fontFamily="sans-serif-condensed-medium"/>

    </LinearLayout>
    <ImageView
        android:id="@+id/audio_imageview"
        android:layout_width="match_parent"
        android:layout_height="400dp"
        android:layout_gravity="center"
        android:layout_marginTop="60dp"
        android:src="@drawable/img" />
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="40dp"
        android:id="@+id/layout_seekbar"
        android:orientation="vertical"
        android:layout_below="@+id/audio_imageview"
        android:gravity="center_vertical"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp"
        android:layout_marginTop="10dp">

        <SeekBar
            android:layout_width="match_parent"
            android:layout_height="40dp"
            android:id="@+id/audio_seekbar"
            android:layout_weight="1"/>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_margin="5dp">
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/player_position"
                android:text="00.00"
                android:textSize="15dp"
                android:textColor="@color/black"
                android:textStyle="bold"
                android:textAlignment="viewStart"
                android:layout_weight="1"/>
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/player_duration"
                android:text="00.00"
                android:textSize="15dp"
                android:textColor="@color/black"
                android:textStyle="bold"
                android:layout_weight="1"
                android:textAlignment="viewEnd"/>
        </LinearLayout>
    </LinearLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:id="@+id/buttons"
        android:orientation="horizontal"
        android:gravity="center_vertical"
        android:layout_below="@+id/layout_seekbar"
        android:layout_marginTop="10dp"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp">
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/backward"
            android:id="@+id/backward"
            android:layout_weight="1"/>
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_play"
            android:id="@+id/play"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_pause"
            android:id="@+id/pause"
            android:visibility="gone"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/forward"
            android:src="@drawable/icforward"
            android:layout_weight="1" />
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:orientation="horizontal"
        android:gravity="center_vertical"
        android:layout_below="@+id/buttons"
        android:layout_marginTop="10dp"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp">
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_loop"
            android:id="@+id/loop"
            android:layout_weight="1"/>
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_cut"
            android:id="@+id/cutSong"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/favourite"
            android:src="@drawable/ic_baseline_favorite_border_24"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/shuffle"
            android:src="@drawable/ic_shuffle"
            android:layout_weight="1" />
    </LinearLayout>
</RelativeLayout>

#MainActivity
package com.example.musicplayer;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.widget.ImageView;
import android.widget.SeekBar;
import android.widget.TextView;
import android.widget.Toast;

import java.util.concurrent.TimeUnit;

public class MainActivity extends AppCompatActivity {

    TextView songName, playerPosition, playerDuration;
    SeekBar seekBar;
    ImageView play, pause, forward, backward;
    MediaPlayer mediaPlayer;
    Handler handler = new Handler();
    Runnable runnable;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        songName = findViewById(R.id.tv_songname);
        playerPosition = findViewById(R.id.player_position);
        playerDuration = findViewById(R.id.player_duration);
        seekBar = findViewById(R.id.audio_seekbar);
        play = findViewById(R.id.play);
        pause = findViewById(R.id.pause);
        forward = findViewById(R.id.forward);
        backward = findViewById(R.id.backward);

        mediaPlayer = MediaPlayer.create(this, R.raw.the_kid_laroi);

        runnable = new Runnable() {
            @Override
            public void run() {
                seekBar.setProgress(mediaPlayer.getCurrentPosition());
                handler.postDelayed(this, 500);


            }
        };

        int duration = mediaPlayer.getDuration();
        String sDuration = convertFormat(duration);
        playerDuration.setText(sDuration);

        play.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                play.setVisibility(View.GONE);
                pause.setVisibility(View.VISIBLE);
                //start media player
                mediaPlayer.start();

                seekBar.setMax(mediaPlayer.getDuration());
                handler.postDelayed(runnable, 0);

                songName.setText("The Kid Laroi,Justin Bieber-Stay");


            }
        });

        pause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                pause.setVisibility(View.GONE);
                play.setVisibility(View.VISIBLE);
                mediaPlayer.pause();
                handler.removeCallbacks(runnable);
            }
        });

        forward.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                int currentPosition = mediaPlayer.getCurrentPosition();
                int duration = mediaPlayer.getDuration();
                if (mediaPlayer.isPlaying() && duration != currentPosition) {
                    currentPosition = currentPosition + 5000;

                    playerPosition.setText(convertFormat((currentPosition)));
                    mediaPlayer.seekTo(currentPosition);
                }
                else
                {
                    Toast.makeText(MainActivity.this,"Cannot Jump Forward 5 Second",Toast.LENGTH_SHORT).show();
                }

            }
        });

        backward.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                int currentPosition = mediaPlayer.getCurrentPosition();
                if (mediaPlayer.isPlaying() && currentPosition > 5000) {
                    currentPosition = currentPosition - 5000;
                    playerPosition.setText(convertFormat(currentPosition));
                    mediaPlayer.seekTo(currentPosition);
                }
                else
                {
                    Toast.makeText(MainActivity.this,"Cannot Jump Backward 5 second",Toast.LENGTH_SHORT).show();
                }
            }
        });

        seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {

                if (fromUser) {
                    mediaPlayer.seekTo(progress);
                }
                playerPosition.setText(convertFormat(mediaPlayer.getCurrentPosition()));

            }

            @Override
            public void onStartTrackingTouch(SeekBar seekBar) {

            }

            @Override
            public void onStopTrackingTouch(SeekBar seekBar) {

            }
        });

        mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
            @Override
            public void onCompletion(MediaPlayer mediaPlayer) {

                pause.setVisibility(View.GONE);
                play.setVisibility(View.VISIBLE);
                mediaPlayer.seekTo(0);
            }


        });
    }

    @SuppressLint("DefaultLocale")
    private String convertFormat(int duration) {
        return String.format("%02d:%02d",
                TimeUnit.MILLISECONDS.toMinutes(duration),
                TimeUnit.MILLISECONDS.toSeconds(duration) -

                        TimeUnit.MINUTES.toSeconds(TimeUnit.MILLISECONDS.toMinutes(duration)));

    }
}

