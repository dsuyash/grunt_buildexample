module.exports = function(grunt) {
 
  // configure the tasks
  grunt.initConfig({
 
    copy: {
      build: {
        cwd: 'app',
        src: [ '**'],
        dest: 'build',
        expand: true
      },
    },
 
    clean: {
      build: {
        src: [ 'build' ]
      },
      stylesheets: {
        src: [ 'build/**/*.css', '!build/css/application.css' ]
      },
      scripts: {
        src: [ 'build/**/*.js', '!build/js/application.js','!build/lib/**' ]
      },
    },
 
    
    cssmin: {
      build: {
        files: {
          'build/css/application.css': [ 'build/css/*.css' ]
        }
      }
    },
 
    uglify: {
      build: {
        options: {
          mangle: false
        },
        files: {
          'build/js/application.js': [ 'build/js/*.js' ]
        }
      }
    },
 
    watch: {
      stylesheets: {
    	files: 'app/**/*.cs',
    	tasks: [ 'stylesheets' ]
  	},
     scripts: {
    	files: 'app/**/*.js',
    	tasks: [ 'scripts' ]
  	},
     copy: {
    	files: [ 'app/**' ],
    	tasks: [ 'copy' ]
  	},
      cssmin:{
        files: [ 'build/**' ],
    	tasks: [ 'cssmin' ]
      },
      scripts:{
        files: [ 'build/**' ],
    	tasks: [ 'scripts' ]
      }
    },
   
    connect: {
      server: {
        options: {
          port: 4000,
          base: 'build',
          hostname: '*'
        }
      }
    }
 
  });
 
  // load the tasks
  grunt.loadNpmTasks('grunt-contrib-copy');
  grunt.loadNpmTasks('grunt-contrib-clean');
  grunt.loadNpmTasks('grunt-contrib-cssmin')
  grunt.loadNpmTasks('grunt-contrib-uglify');
  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-connect');
 
  // define the tasks
  grunt.registerTask(
    'stylesheets', 
    'Compiles the stylesheets.', 
    [ 'cssmin', 'clean:stylesheets' ]
  );
 
  grunt.registerTask(
    'scripts', 
    'Compiles the JavaScript files.', 
    [  'uglify', 'clean:scripts' ]
  );
 
  grunt.registerTask(
    'build', 
    'Compiles all of the assets and copies the files to the build directory.', 
    [ 'clean:build', 'copy','stylesheets', 'scripts']
  );
 
  grunt.registerTask(
    'default', 
    'Watches the project for changes, automatically builds them and runs a server.', 
    [ 'clean:build', 'copy', 'stylesheets', 'scripts', 'connect', 'watch' ]
  );
};
